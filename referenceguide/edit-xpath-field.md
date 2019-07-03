---
id: edit-xpath-field
title: Edit XPath Field
sidebar_label: Edit XPath Field
---
#### XPath data type
Data type of the input.

Currently Date is not implemented.

String: Any text
Long: Integer number
Double: Decimal number

#### Alignment
Alignment of the XPath field.

Default is right aligned.

#### Positive number markup
Precedes positive numbers with a '+' or '  '.

#### Negative number markup
Contain negative numbers within parathesis.

#### Use local group separator
If 'true' the thousand separator mark and the decimal separator mark will be replaced with the locale separator.

e.g. if the Locale is Dutch the decimal separator will be ',' and the thousand separator will be '.' Where if the Locale is US English the decimal separator will be '.' and the thousand separator will be ','.

#### Decimal numbers
The amount of decimal numbers in the output.

#### Use default values
If 'true', when the XPath expression for determining the field value has no result (i.e. the path doesn't exist) a default value is used instead. For a number field this default value is zero (0), for string fields the empty string ("") and for date values the 'zero date' (midnight, January 1, 1970 UTC).

If 'false', when the XPath expression for determining the field value has no result a runtime exception is thrown.

Default is 'false'.

