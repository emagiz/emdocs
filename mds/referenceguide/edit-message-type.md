---
id: edit-message-type
title: Edit message type
sidebar_label: Edit message type
---
#### Display name
Display name for this message type.

This value is used for displaying in the GUI only.

#### Technical name
Abbreviated name of the message type, with a maximum length of eight characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Description
Short description of the message type.

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

#### Amount/frequency of messages?
Example answer:

-About 200 per day
-100 per day but can be 1000 in case of errors

#### Timing/spread of messages?
Example answer:

-Mainly between 09.00 and 17.00


#### Batch: is this really needed and why?
Example answer:

-No, but makes it clearer


#### Size of messages?
Example answer:

-15 rows
-50 KiB per message


#### How critical are the messages? (time & guaranteed delivery)
Example answer:

Time aspect
-Have to be handled within 5 min
-May not get lost, cannot be recreated

Guaranteed delivery
-very, if an order is lost it won't be planned

#### Is the order of messages relevant and why?
Example answer:

-Yes time of entry is leading for handling

#### Additional information 
Additional information

#### Display Name
Display name for this message type.

This value is used for displaying in the GUI only.

#### Description
Short description of the message type.

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

#### Amount/frequency of messages?
Example answer:

-About 200 per day
-100 per day but can be 1000 in case of errors

#### Timing/spread of messages?
Example answer:

-Mainly between 09.00 and 17.00


#### Batch: is this really needed and why?
Example answer:

-No, but makes it clearer


#### Size of messages?
Example answer:

-15 rows
-50 KiB per message


#### How critical are the messages? (time & guaranteed delivery)
Example answer:

Time aspect
-Have to be handled within 5 min
-May not get lost, cannot be recreated

Guaranteed delivery
-very, if an order is lost it won't be planned

#### Is the order of messages relevant and why?
Example answer:

-Yes time of entry is leading for handling

#### Additional information 
Additional information

---
id: edit-message-type
title: Edit message type
sidebar_label: Edit message type
---
#### Display name
Display name for this message type.

This value is used for displaying in the GUI only.

#### Technical name
Abbreviated name of the message type, with a maximum length of eight characters.

This value will be used when auto-generating names for bus components, and must therefore adhere to the naming convensions (use only lower case letters, digits or the '-' character).

#### Description
Short description of the message type.

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

#### Amount/frequency of messages?
Example answer:

-About 200 per day
-100 per day but can be 1000 in case of errors

#### Timing/spread of messages?
Example answer:

-Mainly between 09.00 and 17.00


#### Batch: is this really needed and why?
Example answer:

-No, but makes it clearer


#### Size of messages?
Example answer:

-15 rows
-50 KiB per message


#### How critical are the messages? (time & guaranteed delivery)
Example answer:

Time aspect
-Have to be handled within 5 min
-May not get lost, cannot be recreated

Guaranteed delivery
-very, if an order is lost it won't be planned

#### Is the order of messages relevant and why?
Example answer:

-Yes time of entry is leading for handling

#### Additional information 
Additional information

#### Display Name
Display name for this message type.

This value is used for displaying in the GUI only.

#### Description
Short description of the message type.

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

#### Amount/frequency of messages?
Example answer:

-About 200 per day
-100 per day but can be 1000 in case of errors

#### Timing/spread of messages?
Example answer:

-Mainly between 09.00 and 17.00


#### Batch: is this really needed and why?
Example answer:

-No, but makes it clearer


#### Size of messages?
Example answer:

-15 rows
-50 KiB per message


#### How critical are the messages? (time & guaranteed delivery)
Example answer:

Time aspect
-Have to be handled within 5 min
-May not get lost, cannot be recreated

Guaranteed delivery
-very, if an order is lost it won't be planned

#### Is the order of messages relevant and why?
Example answer:

-Yes time of entry is leading for handling

#### Additional information 
Additional information

