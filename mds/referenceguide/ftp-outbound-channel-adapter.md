---
id: ftp-outbound-channel-adapter
title: FTP outbound channel adapter
sidebar_label: FTP outbound channel adapter
---
#### Write messages to a remote FTP directory.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/ftp.html#ftp-outbound" target="_blank">Documentation</a>

It connects to the FTP server and initiate an FTP transfer for every file it receives in the payload of incoming Messages. 

The FTP Outbound Channel Adapter supports the following payloads: 

<code>java.io.File</code> - the actual file object 
<code>byte[]</code> - a byte array that represents the file contents
<code>java.lang.String</code> - text that represents the file contents 


#### Remote directory
Identifies directory path where file will be transferred to.

e.g., <code>/temp/mytransfers</code>

Mutually exclusive with the <i>remote directory expression</i> setting.

#### Auto create directory
Specify whether to automatically create the remote target directory if it doesn't exist.

Default is <code>false</code>.

#### FTP session factory
FTP session factory that provides the FTP(S) connections for this channel adapter.

<i>Required</i>

#### Mode
Determines the behaviour of this adapter when the destination file already exists.

<b>Replace</b> (default): If the target file already exists, it will be overwritten.

<b>Append</b>: If append is specified, the data will be appended to the existing file if such file exists, otherwise the new file will be created as usual but, once created, the subsequent data will be appended to it. This attribute is mutually exclusive the use of a temporary file, since append is done to the actual file and not its temporary counterpart. If set to <i>Append</i>, the component will also use an instance of the <code>LockRegistry</code> to ensure that there are no collisions when multiple threads are writing to the same file.

<b>Append no flush</b>: Same as <i>Append</i> but the data is not flushed or the file closed. This can significantly improve performance at the risk of lost data in the event of a failure. See also <i>flush interval</i>.

<b>Fail</b>: If the target file exists, a <code>MessageHandlingException</code> is thrown.

<b>Ignore</b>: If the target file exists, the message payload is silently ignored.

#### Remote filename generator
Specifies a file name generator.

If empty, the default file name generator will be used. 

<i>The default generator first checks for a message name in the message header. 
If no name is available it checks if the Message payload is a File instance, and if so, it uses the same name. Finally, it falls back to the Message ID and adds the suffix '.msg'. </i>

Mutually exclusive with the <i>remote filename generator expression</i> setting.

#### Remote filename generator expression
Allows you to provide SpEL expression which will compute file name of the remote file (e.g., assuming payload is a <code>java.io.File</code>: <code>payload.getName() + '.transfered'</code>).

Mutually exclusive with the <i>remote filename generator</i> setting.

#### Remote file separator
Allows you to provide remote file/directory separator character.

Default when empty: <code>/</code>

#### Remote directory expression
Allows you to provide a SpEL expression which will compute the directory path where the files will be transferred to (e.g., <code>headers['remote_dir'] + '/myTransfers'</code>).

Mutually exclusive with the <i>remote directory</i> setting.

#### Charset
Character set to be used in case of a String payload. 

Default when empty: <code>UTF-8</code>

#### Use temporary file name
Allows you to suppress using a temporary file name while writing the file by setting this to false.

Default is <code>true</code>.

#### Temporary file suffix
Extension used when uploading files. We change it right after we know it's uploaded.

Default is <code>.writing</code>.

#### Temporary remote directory
Identifies the remote temporary directory path (e.g., <code>/remote/temp/mytransfers</code>).

If not specified (the default), the file (with the <i>temporary file suffix</i>) will be uploaded to the <i>remote directory</i> directly.

Mutually exclusive with the <i>temporary remote directory expression</i> setting.

#### Temporary remote directory expression
Allows you to provide a SpEL expression which will compute the temporary directory path where files will be transferred to before they are moved to the <i>remote directory</i> (e.g., <code>headers['remote_dir'] + '/temp/myTransfers'</code>).

Mutually exclusive with the <i>temporary remote directory</i> setting.

#### Channel
Channel to consume messages from.

<i>Required</i>


Advice can be added to change the behaviour of this endpoint, for example to add retry logic in case of failures. The following types of advice are available:

<b>Retry advice</b>: allows configuration of sophisticated retry scenarios; this includes specifying policies for retry attemps, backoff periods between attempts and the recovery strategy when retries are exhausted
<b>Circuit breaker</b>: if a certain number of consecutive attempts fails, new requests will <i>fail fast</i> and no attempt will be made to invoke the request handler again until some time has expired
<b>Expression evaluating advice</b>: general advice that evaluates a configurable <i>SpEL expression</i> on successful and/or failed attempts, and optionally can send a message to a <i>success channel</i> and/or <i>failure channel</i>

By adding multiple advices to this endpoint you can create even more complex combined behaviour. For example, if you add a <i>circuit breaker</i> and a <i>retry advice</i>, you can create a scenario where the circuit breaker only opens when all retries are exhaused. Note that the order of the advice types is important, as switching the order will change the combined behaviour: the first item in the list will be the top of the advice chain, meaning it will be the last advice that is evaluated. Also note that if any advice "traps" exceptions, all advices higher up in the chain won't know about any failures.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

