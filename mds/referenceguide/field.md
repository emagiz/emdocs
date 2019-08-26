---
id: field
title: Field
sidebar_label: Field
---
#### XML tag
Tag name for this field's XML element.

<i>Required</i>

#### Documentation
Documentation describing this field.

<i>Optional</i>

#### Has components
Whether this field consists of (multiple) components, or contains just a single value.

#### Required
Whether the value for this field is required or not.

Default is <i>false</i>.

#### Data type
The <i>XML Schema</i> data type of this field.

This data type is only used for data validation, not for data conversion: if the EDI data doesn't exactly correspond to any of the <i>XML Schema</i> formats, use <code>xs:string</code> instead (or just don't specify any type at all).

<i>Optional</i>

#### Min length
The minimum number of characters allowed in the value.

This data type is only used for data validation, not for data conversion (i.e. data won't be padded to fit).

<i>Optional</i>

#### Max length
The maximum number of characters allowed in the value.

This data type is only used for data validation, not for data conversion (i.e. data won't be truncated to fit).

<i>Optional</i>

#### Truncatable
Whether it's allowed to omit trailing empty components (that are not required) for this field.

Note that components that are <i>required</i> can never be omitted.

Default is <i>false</i>.


The different components that can appear in this field, in the order specified.

In the following example, the <code>ADDRESS</code> segment consists of the fields <i>street</i>, <i>town</i> and <i>postcode</i> (field separator is a semicolon), where the <i>street</i> field consists of the components <i>number</i> and <i>street name</i> (component separator is a colon):

<pre>ADDRESS;3:High Street;SOUTHAMPTON;SO31 4NG</pre>

---
id: field
title: Field
sidebar_label: Field
---
#### XML tag
Tag name for this field's XML element.

<i>Required</i>

#### Documentation
Documentation describing this field.

<i>Optional</i>

#### Has components
Whether this field consists of (multiple) components, or contains just a single value.

#### Required
Whether the value for this field is required or not.

Default is <i>false</i>.

#### Data type
The <i>XML Schema</i> data type of this field.

This data type is only used for data validation, not for data conversion: if the EDI data doesn't exactly correspond to any of the <i>XML Schema</i> formats, use <code>xs:string</code> instead (or just don't specify any type at all).

<i>Optional</i>

#### Min length
The minimum number of characters allowed in the value.

This data type is only used for data validation, not for data conversion (i.e. data won't be padded to fit).

<i>Optional</i>

#### Max length
The maximum number of characters allowed in the value.

This data type is only used for data validation, not for data conversion (i.e. data won't be truncated to fit).

<i>Optional</i>

#### Truncatable
Whether it's allowed to omit trailing empty components (that are not required) for this field.

Note that components that are <i>required</i> can never be omitted.

Default is <i>false</i>.


The different components that can appear in this field, in the order specified.

In the following example, the <code>ADDRESS</code> segment consists of the fields <i>street</i>, <i>town</i> and <i>postcode</i> (field separator is a semicolon), where the <i>street</i> field consists of the components <i>number</i> and <i>street name</i> (component separator is a colon):

<pre>ADDRESS;3:High Street;SOUTHAMPTON;SO31 4NG</pre>

