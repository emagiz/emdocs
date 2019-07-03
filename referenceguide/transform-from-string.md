---
id: transform-from-string
title: Transform from string
sidebar_label: Transform from string
---
### 
Starting position for the substring. The first character has position 1, the second position 2, etc.

Example: with start position <code>2</code>, the string <code>eMagiz</code> will be transformed to <code>Magiz</code>.

### 
Where to start counting the characters to find the start position. When selecting <b>from end</b> the last character has position 1, the second to last character has position 2, etc.

Example: with start position <code>2</code> <b>from end</b>, the string <code>eMagiz</code> will be transformed to <code>iz</code>.

### 
Length of the substring to return. If empty, this returns the substring from the start position to the end of the string.

Example: with start position <code>2</code> and length <code>4</code>, the string <code>eMagiz</code> will be transformed to <code>Magi</code>.

### 
All occurrences of characters in the input string that match this regular expression will be replaced.

Example: with regex <code>[aeiou]</code> and an empty replacement value, the string <code>eMagiz</code> will be transformed to <code>Mgz</code>.

See also: <u><a href="https://www.w3.org/TR/xpath-functions/#regex-syntax" target="_blank">W3C regular expression syntax</a></u>

### 
String to replace all characters that matched the regular expression with. Leaving this empty will replace them with an empty string.

Can also contain backreferences to capturing groups in the regular expression by using the <code>$n</code> notation, where 'n' is the group number.

Example: with regex <code>(.*) - (.*)</code> and replacement <code>$2 - $1</code>, the string <code>eMagiz - Platypus</code> will be transformed to <code>Platypus - eMagiz</code>.

See also: <u><a href="https://www.w3.org/TR/xpath-functions/#func-replace" target="_blank">W3C XPath functions reference</a></u>

#### Transformer with multiple options for converting string values.


Transformer with multiple options for converting string values.

Option <b>substring</b> allows you to extract part of a value, for example select only the first 10 characters of a longer string value.

With <b>regex replace</b> you can perform complex find-and-replace operations on string values.

With <b>convert datatype</b> you can convert a string input to another data type. Currently it is only possible to convert to date/time data types.

Selecting <b>custom XPath</b> allows you to fully control the transformation of any value by entering your own custom XPath expression to handle the conversion. Technically, the XPath you enter will be used for the <code>&lt;xsl:value-of&gt;</code> statement in the generated stylesheet. Use the <i>view XSLT</i> button to see a preview how your XPath will be embedded in the resulting XSLT.

### 
Date format 


### 
Date and time format delimiter

### 
Time format

### 
Time zone format 

### 
The time zone to use when converting the input string. If the input string has time zone information, you can preserved it by leaving this field empty, otherwise it will overwrite the zone information with the selected value.

### 
Pattern to use for converting the string value into a date/time data type. The pattern is created based on your date, time,  timezone, and delimiters selection. You can create your own custom format by using the generated pattern as a starting point.

More information about the pattern format syntax can be found in the <a href="http://joda-time.sourceforge.net/apidocs/org/joda/time/format/DateTimeFormat.html" target="_blank">Documentation</a>

### 
Date/time and zone format delimiter

### 
Allows you to fully control the transformation of an attribute value by specifying custom XPath.

You can use the token [%previousOutput%] to refer to the previous generated XPath and use it in the current transformer, e.g. <b>if ([%previousOutput%]!='') then [%previousOutput%] else 'test' </b>

See also: <u><a href="https://www.w3.org/TR/xpath/" target="_blank">W3C XPath specification</a></u>

