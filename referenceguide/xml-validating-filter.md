---
id: xml-validating-filter
title: XML validating filter
sidebar_label: XML validating filter
---
#### Filters XML messages by validating them against a pre-defined XSD.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/xml.html#xml-validating-filter" target="_blank">Documentation</a>

Filters XML messages by validating them against an XSD schema. If the XML is valid, the message will be send to the <i>output channel</i>, otherwise it will be dropped, rejected or send to the <i>discard channel</i>.

#### Custom validation
Custom validation will allow you to specify the location of the xsd. 

By default this will be the <i>resource</i> folder.

#### Definition location
Location of the XSD schema file.

#### XML definition
Select the xml definition that will be used for the validation of your xml message.

This can either be an XML definition or an xsd.

You can create new xml definitions in the resources tab.

#### Schema type
Specifies the xml schema type.

Possible types :
<code>xml-schema</code> - Default
<code>relax-ng</code>

#### Throw exception on rejection
Throw an exception when the input message is invalid. This will cause any error handling on the current message flow to trigger.

Note that when set to <code>true</code>, no messages will be send to the <i>discard channel</i>.

#### Discard channel
Channel where messages should be sent if the filter rejects the message. If no discard channel is set, rejected messages are silently dropped.

<i>Optional</i>

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

