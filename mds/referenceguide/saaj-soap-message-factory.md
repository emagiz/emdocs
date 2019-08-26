---
id: saaj-soap-message-factory
title: SAAJ SOAP message factory
sidebar_label: SAAJ SOAP message factory
---
#### Factory for creating SOAP messages using SAAJ (SOAP with Attachments API for Java).
<a href="http://docs.spring.io/spring-ws/sites/2.0/reference/html/common.html#d0e1162" target="_blank">External documentation</a>

SAAJ (SOAP with Attachments API for Java) specific implementation of the <i>WebServiceMessageFactory</i>. Uses SOAP version 1.1 by default, but can be configured to use SOAP version 1.2 instead.

This factory will use SAAJ 1.3 when found, or fall back to SAAJ 1.2 or even 1.1.

#### SOAP version
Which SOAP version this factory will use. Default is <i>SOAP 1.1</i>.

Even though both versions of SOAP are quite similar in format, the 1.2 version is <b>not</b> backwards compatible with 1.1. The main differences are:
- <b>XML namespace</b>: <code>"http://schemas.xmlsoap.org/soap/envelope/"</code> (SOAP 1.1) vs <code>"http://www.w3.org/2003/05/soap-envelope"</code> (SOAP 1.2)
- <b>Content-Type HTTP header</b>: <code>"text/xml"</code> (SOAP 1.1) vs <code>"application/soap+xml"</code> (SOAP 1.2)
- <b>&lt;soap:Fault&gt;</b>: the structure of this XML element is different
- <b>SOAPAction HTTP header</b>: no longer used by SOAP 1.2

One important thing to note with SOAP version numbers, or <i>WS-*</i> specification version numbers in general, is that the latest version of a specification is generally not the most popular version. For SOAP, this means that currently, the best version to use is 1.1. Version 1.2 might become more popular in the future, but currently 1.1 is the safest bet.

#### Lang attribute on SOAP 1.1 Fault string
Whether a <code>xml:lang</code> attribute should be set on SOAP 1.1 <code>&lt;faultstring&gt;</code> elements.

The default is <i>true</i> to comply with WS-I, but this flag can be set to <i>false</i> for the older W3C SOAP 1.1 specification.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: saaj-soap-message-factory
title: SAAJ SOAP message factory
sidebar_label: SAAJ SOAP message factory
---
#### Factory for creating SOAP messages using SAAJ (SOAP with Attachments API for Java).
<a href="http://docs.spring.io/spring-ws/sites/2.0/reference/html/common.html#d0e1162" target="_blank">Documentation</a>

SAAJ (SOAP with Attachments API for Java) specific implementation of the <i>WebServiceMessageFactory</i>. Uses SOAP version 1.1 by default, but can be configured to use SOAP version 1.2 instead.

This factory will use SAAJ 1.3 when found, or fall back to SAAJ 1.2 or even 1.1.

#### SOAP version
Which SOAP version this factory will use. Default is <i>SOAP 1.1</i>.

Even though both versions of SOAP are quite similar in format, the 1.2 version is <b>not</b> backwards compatible with 1.1. The main differences are:
- <b>XML namespace</b>: <code>"http://schemas.xmlsoap.org/soap/envelope/"</code> (SOAP 1.1) vs <code>"http://www.w3.org/2003/05/soap-envelope"</code> (SOAP 1.2)
- <b>Content-Type HTTP header</b>: <code>"text/xml"</code> (SOAP 1.1) vs <code>"application/soap+xml"</code> (SOAP 1.2)
- <b>&lt;soap:Fault&gt;</b>: the structure of this XML element is different
- <b>SOAPAction HTTP header</b>: no longer used by SOAP 1.2

One important thing to note with SOAP version numbers, or <i>WS-*</i> specification version numbers in general, is that the latest version of a specification is generally not the most popular version. For SOAP, this means that currently, the best version to use is 1.1. Version 1.2 might become more popular in the future, but currently 1.1 is the safest bet.

#### Lang attribute on SOAP 1.1 Fault string
Whether a <code>xml:lang</code> attribute should be set on SOAP 1.1 <code>&lt;faultstring&gt;</code> elements.

The default is <i>true</i> to comply with WS-I, but this flag can be set to <i>false</i> for the older W3C SOAP 1.1 specification.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

