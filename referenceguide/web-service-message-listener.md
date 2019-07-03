---
id: web-service-message-listener
title: Web service message listener
sidebar_label: Web service message listener
---
#### JMS message listener that delegates to a web service message receiver.
<i>JMS message listener</i> that handles incoming JMS messages by passing them to the specified <i>web service message receiver</i>, which can be used to achieve (server-side) <i>SOAP over JMS</i>.

Requires a <i>web service message factory</i> to convert the incoming JMS <code>TextMessage</code> or <code>ByteMessage</code> to a Spring <code>WebServiceMessage</code>.

#### Message receiver
The <i>web service message receiver</i> used by this listener.

<i>Required</i>

#### Message factory
The <i>web service message factory</i> used by this listener.

<i>Required</i>

#### Text message encoding
The encoding used to read from and write to JMS <code>TextMessage</code> messages.

Default is <code>UTF-8</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

