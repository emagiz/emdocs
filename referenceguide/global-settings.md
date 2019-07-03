---
id: global-settings
title: Global settings
sidebar_label: Global settings
---
### 
The XML namespace for the messages described by this definition. Namespaces are used to solve naming conflicts between different definitions by making the names universally unique. For this reason it is strongly recommended to always use namespaces and to follow the best practice of constructing them from your organization's URL.

Some examples:
<code>http://www.my-company.com/ns/my-bus/cdm/1.0/</code>
<code>http://www.my-company.com/ns/my-bus/my-system/1.0/</code>

### 
When a target namespace is provided, this setting determines how the namespace should be applied in XML messages.

<b>Qualified</b> (recommended) means that every element (on any level) in the XML message must use the target namespace. 

<b>Unqualified</b> means that only the root element of the XML message must use the target namespace; all other elements must not use any namespace.

### 
When a target namespace is provided, this setting determines how the namespace should be applied in XML messages. If the option <i>enforce CDM best practices is enabled</i>,  this value is not editable.

<b>Qualified</b> (recommended) means that every element (on any level) in the XML message must use the target namespace. 

<b>Unqualified</b> means that only the root element of the XML message must use the target namespace; all other elements must not use any namespace.

### 
Indicates if eMagiz best practices are applied to this message or not. This value is based on the setting <i>Enforce CDM best practices</i>  from your Design message bus. 

For example, eMagiz autogenerates a namespace based on the provided <i>Namespace URL</i>  and we recommend that every element in the XML message must use the target namespace. Therefore, the <code>xs:elementFormDefault</code> value is not editable. Additionally, the creation of <code>xs:attribute</code> or <code>xs:simpleContent</code> is not allowed. These XSD constructs are not needed for building CDM messages and using them only adds unnecessary complexity to your message.

eMagiz enables the use of best practices by default. If you need to change this setting, you can modify it in the Design bus settings page. Note, that this change will be applied to all your CDM messages.

