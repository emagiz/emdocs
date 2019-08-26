---
id: segment
title: Segment
sidebar_label: Segment
---
#### Segment code
The segment code in the EDI message, i.e. the contents of the first field.

It's also possible to specify a regular expression instead of a normal segment code, in which case the regex is matched against the full segment text.

<i>Required</i>

#### XML tag
Tag name for this segment's XML element.

<i>Required</i>

#### Documentation
Documentation describing this segment.

<i>Optional</i>

#### Min occurs
The minimum number of times this segment must appear (in this position) in the EDI message.

If the entire segment is optional, set this value to <code>0</code>.

Default is <code>1</code>.

#### Max occurs
The maximum number of times this segment can appear (in this position) in the EDI message.

If the entire segment can be repeated an unlimited number of times, set this value to <code>-1</code>.

Default is <code>1</code>.

#### Truncatable
Whether it's allowed to omit trailing empty fields for this segment.

Note that fields that are <i>required</i> can never be omitted.

Default is <i>false</i>.

#### Ignore unmapped fields
If a segment contains fields that are not specified in this EDI mapping, normally this will result in a runtime validation error. By enabling this option, the parser will instead ignore any unmapped trailing fields and continue with the next segment.

Default is <i>false</i>.


The different fields that can appear in this segment, in the order specified.

In the following example, the <code>ADDRESS</code> segment consists of the fields <i>street</i>, <i>town</i> and <i>postcode</i> (field separator is a semicolon):

<pre>ADDRESS;3 High Street;SOUTHAMPTON;SO31 4NG</pre>

---
id: segment
title: Segment
sidebar_label: Segment
---
#### Segment code
The segment code in the EDI message, i.e. the contents of the first field.

It's also possible to specify a regular expression instead of a normal segment code, in which case the regex is matched against the full segment text.

<i>Required</i>

#### XML tag
Tag name for this segment's XML element.

<i>Required</i>

#### Documentation
Documentation describing this segment.

<i>Optional</i>

#### Min occurs
The minimum number of times this segment must appear (in this position) in the EDI message.

If the entire segment is optional, set this value to <code>0</code>.

Default is <code>1</code>.

#### Max occurs
The maximum number of times this segment can appear (in this position) in the EDI message.

If the entire segment can be repeated an unlimited number of times, set this value to <code>-1</code>.

Default is <code>1</code>.

#### Truncatable
Whether it's allowed to omit trailing empty fields for this segment.

Note that fields that are <i>required</i> can never be omitted.

Default is <i>false</i>.

#### Ignore unmapped fields
If a segment contains fields that are not specified in this EDI mapping, normally this will result in a runtime validation error. By enabling this option, the parser will instead ignore any unmapped trailing fields and continue with the next segment.

Default is <i>false</i>.


The different fields that can appear in this segment, in the order specified.

In the following example, the <code>ADDRESS</code> segment consists of the fields <i>street</i>, <i>town</i> and <i>postcode</i> (field separator is a semicolon):

<pre>ADDRESS;3 High Street;SOUTHAMPTON;SO31 4NG</pre>

