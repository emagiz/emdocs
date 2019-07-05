---
id: file-outbound-channel-adapter
title: File outbound channel adapter
sidebar_label: File outbound channel adapter
---
#### Write messages to a file in a specified system directory
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/files.html#file-writing" target="_blank">Documentation</a>


#### Directory
Destination directory where the files will be written to.

Some examples:
- <code>C:/files/out</code>
- <code>${file.base-dir}/my-files/out</code>
- <code>${file.dir.out}</code>

#### Auto create directory
Specify whether to automatically create the destination directory if it does not yet exist when this adapter is being initialized. 

If set to <i>false</i> and the directory does not exist upon initialization, an exception will be thrown.

Default is <i>true</i>.

#### Delete source files
Specify whether to delete source files after writing to the destination directory.

This will only take effect if the message payload is the actual source <code>File</code> instance
 or if the original <code>File</code> instance (or its path) is available in the header.

Default: <i>false</i>

#### Mode
Determines the behaviour of this adapter when the destination file already exists.

<b>Replace</b> (default): If the target file already exists, it will be overwritten.

<b>Append</b>: If append is specified, the data will be appended to the existing file if such file exists, otherwise the new file will be created as usual but, once created, the subsequent data will be appended to it. This attribute is mutually exclusive the use of a temporary file, since append is done to the actual file and not its temporary counterpart. If set to <i>Append</i>, the component will also use an instance of the <code>LockRegistry</code> to ensure that there are no collisions when multiple threads are writing to the same file.

<b>Append no flush</b>: Same as <i>Append</i> but the data is not flushed or the file closed. This can significantly improve performance at the risk of lost data in the event of a failure. See also <i>flush interval</i>.

<b>Fail</b>: If the target file exists, a <code>MessageHandlingException</code> is thrown.

<b>Ignore</b>: If the target file exists, the message payload is silently ignored.

#### Directory expression
Specifies the output directory using a SpEL expression. This allows you to dynamically specify the output directory on a per message basis. For example a message header can be used for specifying the destination directory at runtime.

#### Filename generator
Specifies a file name generator.
If empty, the default file name generator will be used. 

<i>The default generator first checks for a message name in the message header. 
If no name is available it checks if the Message payload is a File instance, and if so, it uses the same name. Finally, it falls back to the Message ID and adds the suffix '.msg'. </i>

Filename generator is mutually exclusive with Filename generator expression.

#### Filename generator expression
Allows you to provide SpEL expression which will compute file name of the target file.

<i>Optional</i>

Filename generator expression is mutually exclusive with filename generator.

#### Charset
Character set to be used in case of a String payload.

<i>Optional</i>

#### Append new line
Whether to append a new-line after each write.

Default is <code>false</code>.

#### Buffer size
The buffer size to use when writing to files.

Default is <code>8192</code> bytes (8 KiB).

#### Flush interval
When using mode <i>append no flush</i> if this time (in milliseconds) elapses without any new writes, the data is flushed and the file closed. This is approximate and may be up to 1.33x this time.

Default is <code>30000</code> ms (30 seconds).

#### Flush when idle
When using mode <i>append no flush</i>, set to <code>false</code> to indicate the <i>flush interval</i> starts from the first new write to a previously flushed (or new) file. When <code>true</code>, the interval starts from the last write (the file is flushed if it has no writes during the interval).


Default is <code>true</code>.

#### Preserve timestamp
Specify whether to preserve the modified timestamp from the source file on the destination file after copying. Applies to <code>java.io.File</code> payloads. For other payload types, the optional <code>file_setModified</code> header will be used, if present, to set the last modified time.

By default, the timestamp will not be preserved.

#### Temporary file suffix
Extension used when writing files. We change it right after we know the file content has been written.

This attribute is mutualy exclusive with mode <i>Append</i>, since the append is done to the actual file and not its temporary counterpart.

Default is <code>.writing</code>.

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

