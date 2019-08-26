---
id: edi-mapping
title: EDI mapping
sidebar_label: EDI mapping
---
#### XML tag
Tag name for the root XML element.

<i>Required</i>

#### Documentation
Documentation describing this EDI mapping.

<i>Optional</i>


The different types of segments ("records" / "lines") that can appear in the EDI message.

These segments must appear in the order indicated <b>before</b> any of the <i>segment groups</i>.

If multiple segments should be grouped together because they can repeat within the EDI message, use a <i>segment group</i> instead.


In the following example, <code>HEADER</code> should be defined as a <i>segment</i>, while <code>ORDER</code> & <code>PICKUP</code> & <code>DELIVERY</code> should be defined as one <i>segment group</i>:

<pre>HEADER ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...</pre>


The different segment groups that can appear in the EDI message.

These segment groups must appear in the order indicated <b>after</b> any of the <i>segments</i>.


In the following example, <code>HEADER</code> should be defined as a <i>segment</i>, while <code>ORDER</code> & <code>PICKUP</code> & <code>DELIVERY</code> should be defined as one <i>segment group</i>:

<pre>HEADER ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...</pre>

#### XML tag
Tag name for the root XML element.

<i>Required</i>

#### Documentation
Documentation describing this EDI mapping.

<i>Optional</i>


The different types of segments ("records" / "lines") that can appear in the EDI message.

These segments must appear in the order indicated <b>before</b> any of the <i>segment groups</i>.

If multiple segments should be grouped together because they can repeat within the EDI message, use a <i>segment group</i> instead.


In the following example, <code>HEADER</code> should be defined as a <i>segment</i>, while <code>ORDER</code> & <code>PICKUP</code> & <code>DELIVERY</code> should be defined as one <i>segment group</i>:

<pre>HEADER ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...</pre>


The different segment groups that can appear in the EDI message.

These segment groups must appear in the order indicated <b>after</b> any of the <i>segments</i>.


In the following example, <code>HEADER</code> should be defined as a <i>segment</i>, while <code>ORDER</code> & <code>PICKUP</code> & <code>DELIVERY</code> should be defined as one <i>segment group</i>:

<pre>HEADER ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...</pre>

#### Segment
Delimiter character(s) separating segments ("records" / "lines") in the EDI format.

The special suffix <code>!$</code> can be added to this delimiter to indicate that the carriage return and life feed characters should be ignored when parsing the segments.

This field supports Java String rules for entering special characters, e.g. <code>\r\n</code> is a "Windows enter".

<i>Required</i>

#### Field
Delimiter character(s) separating fields (within segments) in the EDI format.

This field supports Java String rules for entering special characters, e.g. <code>\t</code> is a tab character.

<i>Required</i>

#### Component
Delimiter character(s) separating components (within fields) in the EDI format.

This field supports Java String rules for entering special characters, e.g. <code>\u00A0</code> is a non-breaking space (using the unicode character notation).

<i>Required</i>

#### Sub-component
Delimiter character(s) separating sub-components (within components) in the EDI format. This is an optional level in the EDI mapping hierarchy.

This field supports Java String rules for entering special characters.

<i>Optional</i>

#### Field repeat
Delimiter character(s) indicating that a field is repeating multiple times within a segment.

This field supports Java String rules for entering special characters.

<i>Optional</i>

#### Escape
Character(s) used to escape any of the other delimiter characters when these appear in the actual data.

This field supports Java String rules for entering special characters, e.g. <code>\\</code> is a backslash.

<i>Optional</i>

#### Segment
Delimiter character(s) separating segments ("records" / "lines") in the EDI format.

The special suffix <code>!$</code> can be added to this delimiter to indicate that the carriage return and life feed characters should be ignored when parsing the segments.

This field supports Java String rules for entering special characters, e.g. <code>\r\n</code> is a "Windows enter".

<i>Required</i>

#### Field
Delimiter character(s) separating fields (within segments) in the EDI format.

This field supports Java String rules for entering special characters, e.g. <code>\t</code> is a tab character.

<i>Required</i>

#### Component
Delimiter character(s) separating components (within fields) in the EDI format.

This field supports Java String rules for entering special characters, e.g. <code>\u00A0</code> is a non-breaking space (using the unicode character notation).

<i>Required</i>

#### Sub-component
Delimiter character(s) separating sub-components (within components) in the EDI format. This is an optional level in the EDI mapping hierarchy.

This field supports Java String rules for entering special characters.

<i>Optional</i>

#### Field repeat
Delimiter character(s) indicating that a field is repeating multiple times within a segment.

This field supports Java String rules for entering special characters.

<i>Optional</i>

#### Escape
Character(s) used to escape any of the other delimiter characters when these appear in the actual data.

This field supports Java String rules for entering special characters, e.g. <code>\\</code> is a backslash.

<i>Optional</i>

#### Name
(Descriptive) name for this EDI mapping.

<i>Required</i>

#### Version
The version of this EDI mapping, e.g. <code>1.0</code>.

<i>Required</i>

#### Namespace
Optional XML namespace for this EDI mapping. When provided, all XML elements defined in this EDI mapping will use this namespace, otherwise they will be namespace-less.

<i>Optional</i>

#### Name
(Descriptive) name for this EDI mapping.

<i>Required</i>

#### Version
The version of this EDI mapping, e.g. <code>1.0</code>.

<i>Required</i>

#### Namespace
Optional XML namespace for this EDI mapping. When provided, all XML elements defined in this EDI mapping will use this namespace, otherwise they will be namespace-less.

<i>Optional</i>

---
id: edi-mapping
title: EDI mapping
sidebar_label: EDI mapping
---
#### XML tag
Tag name for the root XML element.

<i>Required</i>

#### Documentation
Documentation describing this EDI mapping.

<i>Optional</i>


The different types of segments ("records" / "lines") that can appear in the EDI message.

These segments must appear in the order indicated <b>before</b> any of the <i>segment groups</i>.

If multiple segments should be grouped together because they can repeat within the EDI message, use a <i>segment group</i> instead.


In the following example, <code>HEADER</code> should be defined as a <i>segment</i>, while <code>ORDER</code> & <code>PICKUP</code> & <code>DELIVERY</code> should be defined as one <i>segment group</i>:

<pre>HEADER ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...</pre>


The different segment groups that can appear in the EDI message.

These segment groups must appear in the order indicated <b>after</b> any of the <i>segments</i>.


In the following example, <code>HEADER</code> should be defined as a <i>segment</i>, while <code>ORDER</code> & <code>PICKUP</code> & <code>DELIVERY</code> should be defined as one <i>segment group</i>:

<pre>HEADER ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...</pre>

#### XML tag
Tag name for the root XML element.

<i>Required</i>

#### Documentation
Documentation describing this EDI mapping.

<i>Optional</i>


The different types of segments ("records" / "lines") that can appear in the EDI message.

These segments must appear in the order indicated <b>before</b> any of the <i>segment groups</i>.

If multiple segments should be grouped together because they can repeat within the EDI message, use a <i>segment group</i> instead.


In the following example, <code>HEADER</code> should be defined as a <i>segment</i>, while <code>ORDER</code> & <code>PICKUP</code> & <code>DELIVERY</code> should be defined as one <i>segment group</i>:

<pre>HEADER ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...</pre>


The different segment groups that can appear in the EDI message.

These segment groups must appear in the order indicated <b>after</b> any of the <i>segments</i>.


In the following example, <code>HEADER</code> should be defined as a <i>segment</i>, while <code>ORDER</code> & <code>PICKUP</code> & <code>DELIVERY</code> should be defined as one <i>segment group</i>:

<pre>HEADER ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...
ORDER ...
PICKUP ...
DELIVERY ...</pre>

#### Segment
Delimiter character(s) separating segments ("records" / "lines") in the EDI format.

The special suffix <code>!$</code> can be added to this delimiter to indicate that the carriage return and life feed characters should be ignored when parsing the segments.

This field supports Java String rules for entering special characters, e.g. <code>\r\n</code> is a "Windows enter".

<i>Required</i>

#### Field
Delimiter character(s) separating fields (within segments) in the EDI format.

This field supports Java String rules for entering special characters, e.g. <code>\t</code> is a tab character.

<i>Required</i>

#### Component
Delimiter character(s) separating components (within fields) in the EDI format.

This field supports Java String rules for entering special characters, e.g. <code>\u00A0</code> is a non-breaking space (using the unicode character notation).

<i>Required</i>

#### Sub-component
Delimiter character(s) separating sub-components (within components) in the EDI format. This is an optional level in the EDI mapping hierarchy.

This field supports Java String rules for entering special characters.

<i>Optional</i>

#### Field repeat
Delimiter character(s) indicating that a field is repeating multiple times within a segment.

This field supports Java String rules for entering special characters.

<i>Optional</i>

#### Escape
Character(s) used to escape any of the other delimiter characters when these appear in the actual data.

This field supports Java String rules for entering special characters, e.g. <code>\\</code> is a backslash.

<i>Optional</i>

#### Segment
Delimiter character(s) separating segments ("records" / "lines") in the EDI format.

The special suffix <code>!$</code> can be added to this delimiter to indicate that the carriage return and life feed characters should be ignored when parsing the segments.

This field supports Java String rules for entering special characters, e.g. <code>\r\n</code> is a "Windows enter".

<i>Required</i>

#### Field
Delimiter character(s) separating fields (within segments) in the EDI format.

This field supports Java String rules for entering special characters, e.g. <code>\t</code> is a tab character.

<i>Required</i>

#### Component
Delimiter character(s) separating components (within fields) in the EDI format.

This field supports Java String rules for entering special characters, e.g. <code>\u00A0</code> is a non-breaking space (using the unicode character notation).

<i>Required</i>

#### Sub-component
Delimiter character(s) separating sub-components (within components) in the EDI format. This is an optional level in the EDI mapping hierarchy.

This field supports Java String rules for entering special characters.

<i>Optional</i>

#### Field repeat
Delimiter character(s) indicating that a field is repeating multiple times within a segment.

This field supports Java String rules for entering special characters.

<i>Optional</i>

#### Escape
Character(s) used to escape any of the other delimiter characters when these appear in the actual data.

This field supports Java String rules for entering special characters, e.g. <code>\\</code> is a backslash.

<i>Optional</i>

#### Name
(Descriptive) name for this EDI mapping.

<i>Required</i>

#### Version
The version of this EDI mapping, e.g. <code>1.0</code>.

<i>Required</i>

#### Namespace
Optional XML namespace for this EDI mapping. When provided, all XML elements defined in this EDI mapping will use this namespace, otherwise they will be namespace-less.

<i>Optional</i>

#### Name
(Descriptive) name for this EDI mapping.

<i>Required</i>

#### Version
The version of this EDI mapping, e.g. <code>1.0</code>.

<i>Required</i>

#### Namespace
Optional XML namespace for this EDI mapping. When provided, all XML elements defined in this EDI mapping will use this namespace, otherwise they will be namespace-less.

<i>Optional</i>

