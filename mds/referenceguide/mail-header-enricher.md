---
id: mail-header-enricher
title: Mail header enricher
sidebar_label: Mail header enricher
---
#### Configures an outbound MAIL message by adding mail headers.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/mail.html" target="_blank">Documentation</a>

The outbound MailMessage is configured with certain header values. If available, values will be mapped to the outbound mail's properties.

Example:
subject="Example Mail"
to="to@example.org"
cc="cc@example.org"
bcc="bcc@example.org"
from="from@example.org"
reply-to="replyTo@example.org"
overwrite="false"

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

