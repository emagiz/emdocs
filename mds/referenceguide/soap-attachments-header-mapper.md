---
id: soap-attachments-header-mapper
title: SOAP attachments header mapper
sidebar_label: SOAP attachments header mapper
---
#### Maps attachments, as used in the SOAP with Attachments specification, to and from message headers.
<code>SoapHeaderMapper</code> implementation that converts MIME attachments, as used in the <i>SOAP with Attachments</i> (SwA) specification, to and from message headers.

Incoming MIME attachments will converted to message headers, but the (binary) content of the attachments is directly written to disk to prevent reading potentially huge amounts of data into memory. Outgoing MIME attachments will be converted from these same message headers, with the content being read directly from disk. This implies that both the inbound and outbound gateways must have access to the same directory.

The message header used by this header mapper is named <code>emagiz_ws_attachments</code>, with its value being a <code>List</code> of attachments. Each attachment is represented as a <code>Map</code> with the following entries:
- <code>contentId (String)</code>: the (unique) <i>Content-ID</i> of the MIME attachment
- <code>contentType (String)</code>: the <i>Content-Type</i> of the MIME attachment, e.g. <code>application/pdf</code>
- <code>file (File)</code>: the file that contains the (binary) content of the MIME attachment

Normally no attachments equals no <code>emagiz_ws_attachments</code> header on the message, but there is one exception: on the response message of a <i>web service outbound gateway</i> this header is <b>always</b> added, even if there were no MIME attachments in the SOAP response (in this case the header value will be an empty list). This is done to prevent the gateway from copying the original header from the request message to the response message.

When sending attachments with a request, this header mapper will <b>not</b> delete the files containing the content for the MIME attachments, because the web service call might need to be retried later in case of errors. It is up to the user to delete these files after the call succeeded. To make this easier you can use the <code>AttachmentHeader</code> helper class within <i>SpEL</i> expressions. For example, this expression can be used in an <i>expression evaluating request handler advice</i>:
<code>T(com.emagiz.components.ws.AttachmentHeader).copy(headers).deleteFiles()</code>

To populate the <code>emagiz_ws_attachments</code> header without using a <i>web service inbound gateway</i>, you can use the same <code>AttachmentHeader</code> helper class. For example, this expression can be used right after a <i>file inbound channel adapter</i> to create attachment headers for files that are picked up by the adapter:
<code>T(com.emagiz.components.ws.AttachmentHeader).create().add(null, 'image/png', payload).build()</code>

Note that the first argument for <code>add(...)</code>, the <i>Content-ID</i>, is <code>null</code> in this example: this will result in a randomly generated <code>UUID</code> being used. The second argument, the <i>Content-Type</i>, is also optional: if <code>null</code> it will default to <code>application/octet-stream</code>.

To read from the <code>emagiz_ws_attachments</code> header, you can simply use standard <i>SpEL</i> fuctionality. For example, <code>headers.emagiz_ws_attachments[0].file</code> returns the file containing the content of the first MIME attachment.

#### Ignore incoming
Whether to ignore incoming MIME attachments, i.e. not process them at all and (importantly) not save them to disk. If you are only ever <i>sending</i> attachments, set this to <code>true</code>: otherwise you might quickly run out of disk space, because anyone can just send any number of MIME attachments with their requests or responses.

Note that even when setting this to <code>true</code>, response messages of a <i>web service outbound gateway</i> will still have the <code>emagiz_ws_attachments</code> header, with its value being an empty list. This is done to prevent the gateway from copying the original header from the request message to the response message.

Default is <code>false</code>.

#### Directory
The directory where the (binary) content of incoming MIME attachments will be stored as files.

When <i>sending</i> MIME attachments this setting is not used, because the full path to the file location is read from the header information. However, when using a <i>web service inbound gateway</i> paired with a <i>web service outbound gateway</i> to forward attachments, practically speaking both gateways must have (shared) access to this directory. This can be achieved by deploying both on the same server.

This directory is only used when <i>ignore incoming</i> is <code>false</code>, in which case make sure to periodically cleanup old files!

#### Auto create directory
Specify whether to automatically create the directory if it does not yet exist when this header mapper is being initialized.

If set to <code>false</code> and the directory does not exist upon initialization, an exception will be thrown.

Default is <code>true</code>.

#### Delete outgoing reply files
Automatically delete the files on disk containing the contents for the MIME attachments after sending them in a web service <b>response</b>. When using this feature, make sure that your flow does not send any <i>incoming</i> attachments back in the response: this will cause problems as files might be deleted before the attachments have fully been received.

When sending attachments in a web service <b>request</b>, this header mapper will <b>not</b> delete the files containing the content for the MIME attachments, because the web service call might need to be retried later in case of errors. It is up to the user to delete these files after the call succeeded. To make this easier you can use the <code>AttachmentHeader</code> helper class within <i>SpEL</i> expressions. For example, this expression can be used in an <i>expression evaluating request handler advice</i>:
<code>T(com.emagiz.components.ws.AttachmentHeader).copy(headers).deleteFiles()</code>

Regardless of whether you use this feature or not, make sure to periodically cleanup old files as well, otherwise files of messages that do not follow the "happy flow" will remain on disk forever.

Default is <code>true</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

