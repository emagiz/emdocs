---
id: xslt-transformer
title: XSLT transformer
sidebar_label: XSLT transformer
---
#### Transforms XML messages using an XSLT stylesheet.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/xml.html#xml-transformation" target="_blank">Documentation</a>

Transforms XML messages using an XSLT stylesheet.

Transforms the following message payload types:
<code>String</code> - results in <code>String</code> message
<code>org.w3c.dom.Document</code> - results in <code>org.w3c.dom.Document</code> message
<code>javax.xml.transform.Source</code> - results in <code>javax.xml.transform.Result</code>. 

Specify a <i> result transformer</i> to convert to this result to another XML format

#### Custom transformation
Custom transformation will allow you to specify the location of the resource.

By default this will be the <i>resource</i> folder.

#### Transformation location
Filename of the XSLT stylesheet file, including the location.

For example: <code>resources/my-transformation.xsl</code>

#### XML Transformation
Select the xml mapping that will be used to transform your xml message.

This can either be an XML mapping or an xslt.

You can create new xml mappings in the resources tab.

#### Result transformer
Transformer that transforms the result to an alternative (XML) format before it is send on the channel. 

This only works when the input message payload is a <code>java.xml.transform.Source</code> or a <i>result factory</i> is specified, otherwise this transformer does nothing.

If you want to generate a PDF document using XSL-FO, provide a <i>FOP XSL-FO result transformer</i> here (and also set the correct <i>result factory</i>).

#### Result factory
A result factory can prepare the XSLT transformation for a specific output format. Normally, when transforming XML to XML, no result factory is needed.

If you want to generate a PDF document using XSL-FO however, provide a <i>FOP XSL-FO result factory</i> here (and also set the correct <i>result transformer</i>).

#### Transformer factory class
A fully qualified class name to a transformer factory class that overrides the current JVM default.

#### XSLT param headers
Very often to assist with transformation you may need to have access to message data. For example, you may need to get access to certain message headers and pass them on as parameters to a transformer.

If message header names match 1:1 to parameter names, you can simply use this property. It's also possible to use wildcards for simple pattern matching which supports the following simple pattern styles: <code>xxx*</code>, <code>*xxx</code>, <code>*xxx*</code> and <code>xxx*yyy</code>.


Very often to assist with transformation you may need to have access to message data. For example, you may need to get access to certain message headers and pass them on as parameters to a transformer.

With this option you can specify an <i>expression</i> or a <i>value</i>:

An <i>expression</i> should be any valid SpEL expression with <code>Message</code> being the root object of the expression evaluation context. It is also possible to reference any component in a flow using the <code>@</code> notation, e.g. <code>@'full.id.of.your.flow.component'</code>. This can be very useful for passing <i>XSLT extention gateways</i> as parameters to your XSLT.

A <i>value</i> allows you to specify a simple scalar value. You can also use property placeholders (e.g. <code>${some.value}</code>).

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

