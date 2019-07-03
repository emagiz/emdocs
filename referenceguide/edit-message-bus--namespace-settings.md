---
id: edit-message-bus--namespace-settings
title: Edit Message Bus: Namespace settings
sidebar_label: Edit Message Bus: Namespace settings
---
#### Namespace URL
The first part of the namespace for this message bus. Usually the domain name of the company is used, e.g. <i>http://www.mycompany.com/</i>.

This value will be used when auto-generating namespaces for bus components, and must therefore adhere to the naming convensions (starting with <code>http://</code> or <code>https://</code>, followed by a domain name and ending with a slash).

#### Enforce CDM best practices
Indicates if eMagiz best practices are applied to all the CDM messages from the message bus. These best practices are applied to the XML message definitions in the <i>Create</i> phase.

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally,  the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.


