---
id: transform-from-date-time
title: Transform from date/time
sidebar_label: Transform from date/time
---
### 
Transformer with multiple options for converting date/time values.

Option <b>convert datatype</b> allows you to convert XSD date/time data types to XSD string data type.

Option <b>time zone operations</b> allows you to modify the time zone information from a source attribute or the output from a previous operation. These options are only available for <code>xs:dateTime</code>, <code>xs:date</code> and <code>xs:time</code> data types.

Selecting <b>custom XPath</b> allows you to fully control the transformation of any value by entering your own custom XPath expression to handle the conversion. Technically, the XPath you enter will be used for the <code>&lt;xsl:value-of&gt;</code> statement in the generated stylesheet. Use the <i>view XSLT</i> button to see a preview of how your XPath will be embedded in the resulting XSLT.

### 
Currently, it is only possible to do a <b>string</b> conversion. This action will convert the source value to a <code>xs:string</code>

If the source is <code>xs:dateTime</code>, <code>xs:date</code>, or <code>xs:time</code>, you can customize the output format and timezone. For other date/time data types, the conversion will output the attribute's value according to the <code>fn:string</code> function.

For conversions between two date/time attributes, you can add an additional <i>String Transformer</i> with a date/time conversion.

### 
<b>Remove timezone</b> will remove all timezone information from the input date/time without changing its value. For example, applying this function to the <code>xs:dateTime</code> <i>2014-01-01T04:45:30.000+01:00</i> will result in <i>2014-01-01T04:45:30</i>

<b>Adjust to timezone</b> will adjust the given date/time to the specified timezone (respecting the original timezone). For example, applying this function to the <code>xs:dateTime</code> <i>2014-01-01T04:45:30.000+01:00</i> and  'America/New_York' timezone will result in <i>2013-12-31T22:45:30-05:00</i>

#### Transformer with multiple options for converting date/time values.


Transformer with multiple options for converting date/time values.

Option <b>convert datatype</b> allows you to convert XSD date/time data types to XSD string data type.

Option <b>time zone operations</b> allows you to modify the time zone information from a source attribute or the output from a previous operation. These options are only available for <code>xs:dateTime</code>, <code>xs:date</code> and <code>xs:time</code> data types.

Selecting <b>custom XPath</b> allows you to fully control the transformation of any value by entering your own custom XPath expression to handle the conversion. Technically, the XPath you enter will be used for the <code>&lt;xsl:value-of&gt;</code> statement in the generated stylesheet. Use the <i>view XSLT</i> button to see a preview of how your XPath will be embedded in the resulting XSLT.

### 
Date format 


### 
Date and time format delimiter

### 
Time format

### 
Time zone format 

### 
The time zone to use when formatting the output string. If the input has time zone information, you can preserved it by leaving this field empty, otherwise it will use zone information with the selected value.

### 
Pattern to use for formatting the output of a date/time data type. The pattern is created based on your date, time, timezone, and delimiters selection. You can create your own custom format by using the generated pattern as a starting point.

More information about the pattern format syntax can be found in the <u><a href="http://joda-time.sourceforge.net/apidocs/org/joda/time/format/DateTimeFormat.html" target="_blank">Documentation</a></u>

### 
Date/time and zone format delimiter

### 
Allows you to fully control the transformation of an attribute value by specifying custom XPath.

You can use the token [%previousOutput%] to refer to the previous generated XPath and use it in the current transformer, e.g. <b>if ([%previousOutput%]!='') then [%previousOutput%] else 'test' </b>

See also: <u><a href="https://www.w3.org/TR/xpath/" target="_blank">W3C XPath specification</a></u>

