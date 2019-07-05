---
id: file-inbound-channel-adapter
title: File inbound channel adapter
sidebar_label: File inbound channel adapter
---
#### Reads files from the (local) filesystem and creates a message for each file.
<a href="http://docs.spring.io/spring-integration/docs/2.2.6.RELEASE/reference/html/files.html#file-reading" target="_blank">Documentation</a>

Reads files from the (local) filesystem and creates a message for each file.

To prevent creating messages for certain files, this channel adapter has different filtering options. By default, <i>prevent duplicates</i> is enabled: this filter ensures files are picked up only once from the directory.

A common problem with reading files is that a file may be detected before it is ready. The default <i>prevent duplicates</i> does <b>not</b> prevent this. In most cases, this can be prevented if the file-writing process renames each file as soon as it is ready for reading. A <i>filename pattern</i> or <i>filename regex</i> filter that accepts only files that are ready (e.g. based on a known suffix), coupled with the default <i>prevent duplicates</i> filter, allows for this.

#### Directory
Source directory where the files will be read from.

Some examples:
- <code>C:/files/in</code>
- <code>${file.base-dir}/files/in</code>
- <code>${file.dir.in}</code>

#### Filename pattern
Only filenames matching this <i>ant style expression</i> will be picked up by this adapter.

The ant style expression uses the following rules:
- '?' matches one character
- '*' matches zero or more characters

Some examples:
<code>t?st.xml</code> - matches <code>test.xml</code> but also <code>tast.xml</code> or <code>txst.xml</code>
<code>*.xml</code> - matches all <code>.xml</code> files 

Note: Use <i>filename-regex</i> for  for more advanced patterns.

#### Auto create directory
Specify whether to automatically create the source directory if it does not yet exist when this adapter is being initialized. 

If set to <i>false</i> and the directory does not exist upon initialization, an exception will be thrown.

Default is <i>true</i>.

#### Ignore hidden
Whether hidden files shall be ignored by this adapter.

If disabled, hidden files will be processed just like normal files. If enabled, an <code>IgnoreHiddenFileListFilter</code> will be added to filter the hidden files.

Default is <code>true</code>.

#### Prevent duplicates
Specifies whether duplicates should be prevented, by keeping a (unbounded) list of file names in memory and only passing files the first time they are polled.

If enabled, this duplicate prevention is done before any other filtering, i.e. before applying the <i>filename pattern</i>, the <i>filename regex</i> or a custom <i>filter</i>.

Default is <i>true</i>.

#### Filename regex
Only files matching this regular expression will be picked up by this adapter.

Examples:

<code> ^.*\.xml$</code> - matches all <code> .xml</code> files
<code> ^test\d{4}\.xml$</code> - matches all filenames that start with <code>test</code> followed by 4 digits and end with <code> .xml</code>
<code> ${FILENAME_REGEX} </code> - matches all files that match the regular expression inside the global <code>FILENAME_REGEX</code> property

See the Java documentation about patterns:

<a href="http://java.sun.com/javase/6/docs/api/java/util/regex/Pattern.html" target="_blank">Pattern documentation</a>



#### Queue size
Specify the maximum number of file names read into memory when scanning the directory. This is useful to limit the memory footprint of this endpoint.

A larger queue size reduces the number of directory listings needed, but it increases the chances of the internal queue being out of whack with the actual files listed in the directory. Use <code>0</code> for small but volatile directories, use a large number for large directories that are only written to.

Using a stateful filter would counter this benefit, so <i>accept once file list filter</i> is not used when this attribute is specified.

If not specified (the default) all files names are read into memory. This makes it possible to apply stateful filters (such as the <i>accept once file list filter</i>), but this setting should <b>not</b> be used with directories that contain a vast number of files.

#### Filter
You can supply a custom filter to prevent creating messages for certain files. Use this if you need more control over the filtering process than is possible with the <i>filename pattern</i> or <i>filename regex</i> options.

Note that if <i>prevent duplicates</i> is enabled, an <i>accept once file list filter</i> with an unbounded queue is automatically applied before your custom filter is called.

#### Use watch service
By default this channel adapter will scan all items (files and directories!) in the specified source directory, but not in any of its subdirectories. By enabling this option you can change this default behaviour.

The watch service relies on file system events when new files are added to the directory. During initialization, the directory is registered to generate events; the initial file list is also built. While walking the directory tree, any subdirectories encountered are also registered to generate events. On the first poll, the initial file list from walking the directory is returned. On subsequent polls, files from new creation events are returned. If a new subdirectory is added, its creation event is used to walk the new subtree to find existing files, as well as registering any new subdirectories found.

Note that any specified filters are still applied after the watch service returns the list of files.

#### Watch events
Comma-separated list of system event types (<code>CREATE</code>, <code>MODIFY</code>, <code>DELETE</code>) the watch service will listen to.

Default is <code>CREATE</code>.

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

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

