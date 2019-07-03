---
id: message-type
title: Message type
sidebar_label: Message type
---
#### Display name
Display name for this message type.

This value is used for displaying in the GUI only.

#### Name
Abbreviated name of the message type, with a maximum length of eight characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Asynchronous
Whether message flows for this message type are <i>asynchronous</i> ("send and forget") or <i>synchronous</i> ("request/response").

Note that even when using a transport mechanism that is synchronous by nature (e.g. a SOAP web service), the message flow itself can be asynchronous. In these cases the connector will convert the synchronous "request/response" communication into asynchronous "send and forget" behaviour by immediately sending some kind of (dummy) acknowledgements as the response.

If possible, always use <i>asynchronous</i> messaging as it has numerous advantages over <i>synchronous</i> messaging:
 - messages don't (quickly) expire
 - routing to multiple offramps is possible
 - no timeouts/time limits
 - uses less message queues
 - retry/redelivery of messages
 - messages can be made persistent, guaranteeing delivery

