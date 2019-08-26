---
id: attribute
title: Attribute
sidebar_label: Attribute
---
### 
Name of the attribute. Must be unique amongst its siblings.

This will also be the (local) name of the corresponding XSD element.

### 
Whether this attribute is optional (can be omitted) or is required (must always appear).

On the corresponding XSD element, this will result in <code>minOccurs="0"</code> or <code>minOccurs="1"</code> respectively.

### 
In the design phase the data type of this attribute is set to <b>Enumeration</b>.

Here you can set the specific XSD enumeration values for the attribute. You can choose to re-use any existing enumerations in this definition, or create a new one. All enumerations can also be managed from the global settings by clicking the button with the wrench icon to the left.

If no enumeration values are specified, XSD data type <code>xs:string</code> will be used as a fallback.

### 
Specifies a lower bound on a numeric value.  Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies an upper bound on a numeric value. Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies a lower bound on a decimal value.  Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Secifies an upper bound on a decimal value. Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies an lower bound on a period value. Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies an upper bound on a period value.  Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies the maximum number of characters or list items allowed. Must be equal to or greater than zero.

For example if 8  is set as <i> max length</i> value for the attribute <b>password</b>, this means that  the value must be maximum 8 characters,  otherwise the message will be rejected.

### 
Specifies the minimum number of characters or list items allowed. Must be equal to or greater than zero.

For example if 5  is set as <i> min length</i> value for the attribute <b>password</b>, this means that  the value must be minimum five characters,  otherwise the message will be rejected.

### 
Limits the content of an attribute to a specific set of numbers, letters or symbols that satisfy a regular expression. For example if the pattern <code>[A-Z][A-Z][A-Z] </code> is added to the attribute <b>initials</b>, the only acceptable values for this attribute will be 3 uppercase letters from a to z,  otherwise the message will be rejected.

More information about regular expressions and a quick online expression tester can be found
<a href="https://regexr.com/" target="_blank">here</a>


### 
Specifies the exact number of digits allowed. Must be greater than zero

### 
Specifies the maximum number of decimal places allowed. Must be equal to or greater than zero. 
 

### 
Specifies a lower bound on a date/time value. Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies a upper bound on a date/time value.  Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies a lower bound on a date/time value. Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies a upper bound on a date/time value.  Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies a lower bound on a date/time value. Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies a upper bound on a date/time value.  Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies a lower bound on a numeric value.  Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies an upper bound on a numeric value. Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies a lower bound on a decimal value.  Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Secifies an upper bound on a decimal value. Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies an lower bound on a period value. Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies an upper bound on a period value.  Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies the maximum number of characters or list items allowed. Must be equal to or greater than zero.

For example if 8  is set as <i> max length</i> value for the attribute <b>password</b>, this means that  the value must be maximum 8 characters,  otherwise the message will be rejected.

### 
Specifies the minimum number of characters or list items allowed. Must be equal to or greater than zero.

For example if 5  is set as <i> min length</i> value for the attribute <b>password</b>, this means that  the value must be minimum five characters,  otherwise the message will be rejected.

### 
Limits the content of an attribute to a specific set of numbers, letters or symbols that satisfy a regular expression. For example if the pattern <code>[A-Z][A-Z][A-Z] </code> is added to the attribute <b>initials</b>, the only acceptable values for this attribute will be 3 uppercase letters from a to z,  otherwise the message will be rejected.

More information about regular expressions and a quick online expression tester can be found
<a href="https://regexr.com/" target="_blank">here</a>


### 
Specifies the exact number of digits allowed. Must be greater than zero

### 
Specifies the maximum number of decimal places allowed. Must be equal to or greater than zero. 
 

### 
Specifies a lower bound on a date/time value. Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies a upper bound on a date/time value.  Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies a lower bound on a date/time value. Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies a upper bound on a date/time value.  Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Specifies a lower bound on a date/time value. Depending on the selected operator, only values greater or greater and equal to the specified value will be valid. 

Technically it will generate a <code>MinExclusive</code> or <code>MinInclusive</code> restriction in the resulting XSD.

### 
Specifies a upper bound on a date/time value.  Depending on the selected operator, only values less or less and equal to the specified value will be valid. 

Technically it will generate a <code>MaxExclusive</code> or <code>MaxInclusive</code> restriction in the resulting XSD.

### 
Name of the attribute. Must be unique amongst its siblings.

This will also be the (local) name of the corresponding XSD element.

### 
Whether this attribute is optional (can be omitted) or is required (must always appear).

On the corresponding XSD element, this will result in <code>minOccurs="0"</code> or <code>minOccurs="1"</code> respectively.

### 
In the design phase the data type of this attribute is set to <b>Enumeration</b>.

Here you can set the specific XSD enumeration values for the attribute. You can choose to re-use any existing enumerations in this definition, or create a new one. All enumerations can also be managed from the global settings by clicking the button with the wrench icon to the left.

If no enumeration values are specified, XSD data type <code>xs:string</code> will be used as a fallback.

### 
By default an attribute will be represented in the XSD as an <code>xs:element</code>. By enabling this setting the attribute will be represented in the XSD as an <code>xs:attribute</code> instead. Visually this is indicated by an '@' character in front of the attribute name.

Enabling this will also cause either <code>use="optional"</code> or <code>use="required"</code> to be added to the XSD, depending on the value of the <i>optional</i> setting of this attribute.

### 
By default entities will be represented in the XSD as a <code>xs:complexType</code> with a <code>xs:sequence</code> containing all child attributes and entities. Example of such an XML structure:
<i>&nbsp;&nbsp;&lt;Weight&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;Unit&gt;kg&lt;/Unit&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&lt;Value&gt;100&lt;/Value&gt;
&nbsp;&nbsp;&lt;/Weight&gt;</i>

Sometimes an external system requires an entity to be represented in the XSD as a <code>xs:complexType</code> with a <code>xs:simpleContent</code> that extends a simple type. In these specific cases you should switch to using "simple content". The same XML example would then look like this:
<i>&nbsp;&nbsp;&lt;Weight unit="kg"&gt;100&lt;/Weight&gt;</i>

To achieve this for the above example, you'd have to enable <i>XSD simple content</i> for attribute <i>Value</i>. Visually this is indicated by showing the attribute name in parentheses. The following restrictions apply to entities with "simple content":
<ul><li><b>Exactly one</b> attribute may have <i>XSD simple content</i> enabled and must <b>not</b> have <i>XSD attribute</i> enabled</li><li>All other attributes of the same entity <b>must</b> have <i>XSD attribute</i> enabled</li><li>The entity is not allowed to contain any child entities</li></ul>

### 
In the design phase the data type of this attribute is set to <b>Boolean</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>xs:boolean</code>.

### 
In the design phase the data type of this attribute is set to <b>DateTime</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>xs:dateTime</code>.

### 
In the design phase the data type of this attribute is set to <b>Decimal</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>xs:decimal</code>.

### 
In the design phase the data type of this attribute is set to <b>Integer</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>xs:long</code>.

### 
In the design phase the data type of this attribute is set to <b>String</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>nonEmptyString</code>.

### 
In the design phase the data type of this attribute is set to <b>Boolean</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>xs:boolean</code>.

### 
In the design phase the data type of this attribute is set to <b>DateTime</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>xs:dateTime</code>.

### 
In the design phase the data type of this attribute is set to <b>Decimal</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>xs:decimal</code>.

### 
In the design phase the data type of this attribute is set to <b>Integer</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>xs:long</code>.

### 
In the design phase the data type of this attribute is set to <b>String</b>.

Here you can set the specific XSD data type for the attribute. You can only choose from the XSD data types that are a subtype of the design data type.

Default is <code>nonEmptyString</code>.

