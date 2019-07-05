---
id: sub-component
title: Sub-component
sidebar_label: Sub-component
---
#### XML tag
Tag name for this sub-component's XML element.

<i>Required</i>

#### Documentation
Documentation describing this sub-component.

<i>Optional</i>

#### Required
Whether the value for this sub-component is required or not.

Default is <i>false</i>.

#### Data type
The <i>XML Schema</i> data type of this sub-component.

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

