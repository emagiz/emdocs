---
id: jms-xml-message-converter
title: JMS XML message converter
sidebar_label: JMS XML message converter
---
#### A message converter for converting between JMS XML messages and Spring messages.
This converter can transform between JMS  messages and Spring messages in two directions.

<b> Spring to JMS </b> 

The following types of payloads of Spring messages are converted (other types will cause a MessageConversionException): 
 - <i>TextMessage</i>: these objects are returned unchanged (no new message is created) 
 - <i>String</i>: these objects are used as the body for a newly created TextMessage without any alteration (i.e. non-XML strings won't cause errors) 
 - <i>Document, Source</i>: these objects are transformed to a String, which is then used as the XML body for a newly created TextMessage 

<b>JMS to Spring </b> 
The reverse conversion, from JMS Message to String message payload, is only supported for text messages (the other message types will cause a MessageConversionException). 

This conversion just extracts the String body of the message and returns it without any alteration (i.e. non-XML strings won't cause errors).


#### Content type property name
Specifies the name of the JMS property that will be added to newly created TextMessages, indicating the content type of the text. 

This is only used with conversion from Spring to JMS. Only if both the name and the value are set the JMS property will be added. 

Default is empty, which disables the addition of the JMS property to messages.



#### Content type property value
Sets the value of the JMS property that will be added to newly created TextMessages, indicating the content type of the text. 

This is only used with conversion from Spring to JMS. Only if both the name and the value are set the JMS property will be added. 

Default is empty, which disables the addition of the JMS property to messages.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: jms-xml-message-converter
title: JMS XML message converter
sidebar_label: JMS XML message converter
---
#### A message converter for converting between JMS XML messages and Spring messages.
This converter can transform between JMS  messages and Spring messages in two directions.

<b> Spring to JMS </b> 

The following types of payloads of Spring messages are converted (other types will cause a MessageConversionException): 
 - <i>TextMessage</i>: these objects are returned unchanged (no new message is created) 
 - <i>String</i>: these objects are used as the body for a newly created TextMessage without any alteration (i.e. non-XML strings won't cause errors) 
 - <i>Document, Source</i>: these objects are transformed to a String, which is then used as the XML body for a newly created TextMessage 

<b>JMS to Spring </b> 
The reverse conversion, from JMS Message to String message payload, is only supported for text messages (the other message types will cause a MessageConversionException). 

This conversion just extracts the String body of the message and returns it without any alteration (i.e. non-XML strings won't cause errors).


#### Content type property name
Specifies the name of the JMS property that will be added to newly created TextMessages, indicating the content type of the text. 

This is only used with conversion from Spring to JMS. Only if both the name and the value are set the JMS property will be added. 

Default is empty, which disables the addition of the JMS property to messages.



#### Content type property value
Sets the value of the JMS property that will be added to newly created TextMessages, indicating the content type of the text. 

This is only used with conversion from Spring to JMS. Only if both the name and the value are set the JMS property will be added. 

Default is empty, which disables the addition of the JMS property to messages.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

