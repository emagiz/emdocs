---
id: component
title: Component
sidebar_label: Component
---
#### XML tag
Tag name for this component's XML element.

<i>Required</i>

#### Documentation
Documentation describing this component.

<i>Optional</i>

#### Has sub-components
Whether this component consists of (multiple) sub-components, or contains just a single value.

#### Required
Whether the value for this component is required or not.

Default is <i>false</i>.

#### Data type
The <i>XML Schema</i> data type of this component.

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
Whether it's allowed to omit trailing empty sub-components (that are not required) for this component.

Note that sub-components that are <i>required</i> can never be omitted.

Default is <i>false</i>.


The different sub-components that can appear in this field, in the order specified.

---
id: component
title: Component
sidebar_label: Component
---
#### XML tag
Tag name for this component's XML element.

<i>Required</i>

#### Documentation
Documentation describing this component.

<i>Optional</i>

#### Has sub-components
Whether this component consists of (multiple) sub-components, or contains just a single value.

#### Required
Whether the value for this component is required or not.

Default is <i>false</i>.

#### Data type
The <i>XML Schema</i> data type of this component.

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
Whether it's allowed to omit trailing empty sub-components (that are not required) for this component.

Note that sub-components that are <i>required</i> can never be omitted.

Default is <i>false</i>.


The different sub-components that can appear in this field, in the order specified.

