# SFTP inbound channel adapter
#### Synchronizes a remote SFTP directory with a local directory and creates file-messages.
<a href="http://docs.spring.io/spring-integration/docs/2.2.6.RELEASE/reference/html/sftp.html#sftp-inbound" target="_blank">Documentation</a>

The SFTP inbound channel adapter has two tasks: 
- communicate with a remote server in order to transfer files from a remote directory to a local directory
- for each transferred file, generate a message with that file as the payload and send it to the channel

If your local directory already has one or more files it will first generate messages from those, and only when all local files have been processed, it will initiate the remote communication to retrieve more files.


Step-by-step this adapter functions as follows each time it is triggered by the poller to produce a message:

1 - check the local directory for a file to process; all local files are only <b>accepted once</b> based on the file name and files with names ending with the <i>temporary file suffix</i> are ignored, but other than these restrictions <b>every</b> local file is processed

2 - if step 1 finds a suitable local file a message with this file as the payload is created and the adapter is done, otherwise the adapter continues with step 3

3 - synchronize the remote SFTP directory with the local directory:
3a - get a list of all files in the remote SFTP directory that match the (user specified) filter
3b - determine the local file name for each of these remote SFTP files; if a <i>local filename generator expression</i> is specified the evaluation result will be used as the local file name, otherwise the remote SFTP file name is used as the local file name
3c - if a file with the determined local file name already exists in the local directory the remote SFTP file is <b>not transferred</b>; otherwise the remote SFTP file is downloaded to the local directory using a <b>temporary file name</b> (genereted by appending the <i>temporary file suffix</i> to the local file name)
3d - after each successful transfer, the temporary local file is then <b>renamed</b> to the determined local file name and the corresponding remote SFTP file is <b>deleted</b> if the adapter is configured to do so

4 - step 1 is tried again: if this now results in a suitable local file a message with this file as the payload is created, otherwise no message is generated


Note: SFTP = <b>SSH File Transfer Protocol</b>, an extension of the Secure Shell protocol (SSH) to provide secure file transfer capability. Not to be confused with "regular" FTP(S), which is a completely unrelated (and incompatible) file transfer protocol.

Please be aware that, depending on the SSH encryption level used by the server, you might need to install the <i>Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files</i> to successfully establish secure connections.

#### Filename regex
Only files with names matching this regular expression will be picked up by this adapter.

Some examples:
<code>^.*\.xml$</code> - matches all <code> .xml</code> files
<code>^test\d{4}\.xml$</code> - matches all filenames that start with <code>test</code> followed by 4 digits and end with <code> .xml</code>
<code>${FILENAME_REGEX}</code> - matches all files that match the regular expression inside the global <code>FILENAME_REGEX</code> property

See also the <a href="http://java.sun.com/javase/6/docs/api/java/util/regex/Pattern.html" target="_blank">Java documentation</a> about patterns.

It is not possible to use this option together with a <i>filename pattern</i> or a <i>filter</i>.

Note that this filter runs against the <b>remote</b> file system view.

Default is empty (no filter will be applied).

#### Filter
A custom <i>file list filter</i> implementation to determine which files this adapter should pick up.

It is not possible to use this option together with a <i>filename regex</i> or a <i>filename pattern</i>.

Note that this filter runs against the <b>remote</b> file system view.

Default is empty (no filter will be applied).

#### Remote file separator
Allows you to provide remote file/directory separator character.

Default is a forward slash (<code>"/"</code>).

#### Temporary file suffix
Extension used when downloading files. We change it right after we know it's downloaded.

Default is <code>.writing</code>.

#### Local filename generator expression
Allows you to provide a SpEL expression to generate the file name of the local (transferred) file. The root object of the SpEL evaluation is the name of the original file.

For example, a valid expression would be <code>#this.toUpperCase() + '.a'</code> where <code>#this</code> represents the original name of the remote file.

Note that when the local directory is scanned for unprocessed files, each file name is only accepted once and file names ending with the <i>temporary file suffix</i> are ignored.

#### Local filter
Allows you to specify a reference to a custom <i>file list filter</i>. This filter is applied to files after they have been retrieved, i.e. this filter runs against the <b>local</b> file system view.

The default is an <code>AcceptOnceFileListFilter</code> which means that, even if a new instance of a file is retrieved from the remote server, a message won't be generated.

Any filter provided here is combined with a filter that prevents the message source from processing files that are currently being downloaded.

#### Preserve timestamp
Specify whether to preserve the modified timestamp from the remote source file on the local file after copying.

Default is <code>false</code>, meaning the remote timestamp will not be preserved.

#### Remote directory
Identifies the (remote) directory path where files will be transferred <b>from</b>.

For example: <code>/transfers/inbound</code>

<i>Required</i>

#### Local directory
Identifies the (local) directory path where file will be transferred <b>to</b>.

Some examples:
- <code>D:/transfers/inbound</code>
- <code>/tmp/transfers/inbound</code>
- <code>${ftp.dir.local}</code>

<i>Required</i>

#### Filename pattern
Only files with names matching this <i>ant style expression</i> will be picked up by this adapter.

The ant style expression uses the following rules:
<code>?</code> - matches one character
<code>*</code> - matches zero or more characters
 
Some examples:
<code>t?st.xml</code> - matches <code>test.xml</code> but also <code>tast.xml</code> or <code>txst.xml</code>
<code>*.xml</code> - matches all <code>.xml</code> files

It is not possible to use this option together with a <i>filename regex</i> or a <i>filter</i>.

Note that this filter runs against the <b>remote</b> file system view.

Default is empty (no filter will be applied).

#### Auto create local directory
Specify whether to automatically create the local directory if it does not yet exist when this adapter is being initialized. 

If set to <code>false</code> and the directory does not exist upon initialization, an exception will be thrown.

Default is <code>true</code>.

#### Delete remote files
Specify whether to delete the remote source file after copying.

Default is <code>false</code>.

#### SFTP session factory
SFTP session factory that provides the SFTP connections for this channel adapter.

<i>Required</i>


<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-endpoints-chapter.html#endpoint-namespace" target="_blank">Documentation</a>

Specifies when and how the reading task is executed.

Default global poller is used when empty

#### Use default poller
Specifies if the global (default) poller should be used or an included poller.

The poller specifies when and how the reading task is executed.

If the global poller is used it should be added as separate support object.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

#### Trigger type
A <i>trigger</i> specifies the schedule of the <i>poller</i>.

Trigger types:

<b>1. Fixed delay trigger </b>
Triggers with a <i>periodic constant interval</i>. Each execution is scheduled relative to the <i>actual</i> execution time of the previous execution. If an execution is delayed for any reason (such as garbage collection or other background activity), subsequent executions will be delayed as well. 

<b>2. Fixed rate trigger</b>
Triggers with a <i>periodic constant interval</i>. Each execution is scheduled relative to the <i>scheduled</i> execution time of the initial execution.If an execution is delayed for any reason , two or more executions will occur in rapid succession to "catch up."

<b>3. Cron trigger</b>
Enables the scheduling of tasks based on <i>cron expressions</i>.  Consider using a cron trigger for hourly, daily, and monthly settings. 


#### Time unit
Specifies the time unit of the <i>fixed delay</i> or <i>fixed rate</i> value.

For hourly, daily or monthly settings, consider using a <i>cron trigger</i> instead.

Default is <code>Milliseconds</code>.

#### Fixed delay
Time between each two subsequent executions, measured from completion time.

#### Fixed rate
Time between each two subsequent executions, measured from start time.

#### Cron
Pattern used by a cron-trigger to specify the trigger schedule.

The pattern is a list of six single space-separated fields, representing <code>second minute hour day month weekday</code>. Month and weekday names can be given as the first three letters of the English names.

Example patterns:

<code>0 0 * * * *</code> = the top of every hour of every day
<code>0 0 8-10 * * *</code> = 8, 9 and 10 o'clock of every day
<code>0 0/30 8-10 * * *</code> = 8:00, 8:30, 9:00, 9:30 and 10 o'clock every day
<code>0 0 9-17 * * MON-FRI</code> = on the hour nine-to-five weekdays
<code>0 0 0 25 12 ?</code> = every Christmas Day at midnight

#### Max messages per poll
Specifies the <i>maximum number of messages</i> to receive within a given poll operation. 

The poller will continue trying to receive without waiting until either no message is available or this maximum is reached.

For example, if a poller has a 10 second interval trigger and a <i>maxMessagesPerPoll</i> setting of 25, and it is polling a channel that has 100 messages in its queue, all 100 messages can be retrieved within 40 seconds. It grabs 25, waits 10 seconds, grabs the next 25, and so on. 

Default is 1.


#### Receive timeout
Specifies the <i>amount of time</i> the poller should wait if no messages are available when receiving.

#### Send timeout
Specifies the timeout for sending out messages.

#### Task executor
Task executor to execute the scheduled tasks. 

Default when empty: TaskScheduler with name 'taskScheduler', created if not exists.

#### Error channel
The channel that error messages will be sent to if a failure occurs in this poller's invocation. To completely suppress exceptions, provide a reference to the <i>nullChannel</i> here.

