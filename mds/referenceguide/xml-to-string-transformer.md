---
id: xml-to-string-transformer
title: XML to string transformer
sidebar_label: XML to string transformer
---
#### A payload transformer that converts different types of payloads (that represent XML documents) to a String. 
A payload transformer that converts different types of payloads (that represent XML documents) to a string.

This transformer can convert payloads of the following types to a String (other object types will cause an exception):

<i>String:</i> these payloads are simply returned without any alteration (i.e. non-XML strings won't cause errors)
<i>DOM Document:</i> these payloads are transformed to a  <i>String:</i> using the <i>indentity transform</i>, which is then returned
<i>XOM Document:</i> these payloads are transformed to a String by returning the result of calling toXML() on the payload
<i>Source: </i>these payloads are transformed to a  <i>String:</i> using the <i>indentity transform</i>, which is then returned

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

---
id: xml-to-string-transformer
title: XML to string transformer
sidebar_label: XML to string transformer
---
#### A payload transformer that converts different types of payloads (that represent XML documents) to a String. 
A payload transformer that converts different types of payloads (that represent XML documents) to a string.

This transformer can convert payloads of the following types to a String (other object types will cause an exception):

<i>String:</i> these payloads are simply returned without any alteration (i.e. non-XML strings won't cause errors)
<i>DOM Document:</i> these payloads are transformed to a  <i>String:</i> using the <i>indentity transform</i>, which is then returned
<i>XOM Document:</i> these payloads are transformed to a String by returning the result of calling toXML() on the payload
<i>Source: </i>these payloads are transformed to a  <i>String:</i> using the <i>indentity transform</i>, which is then returned

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

