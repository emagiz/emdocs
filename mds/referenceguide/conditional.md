---
id: conditional
title: Conditional
sidebar_label: Conditional
---
### 
Option <b>If exists</b> checks if the source attribute is present in the message or not. Depending on the evaluation of this condition, a different source value is mapped to the destination. If the source attribute is present in the message the source attribute defined in your rule will be used, otherwise the default value will be used. 

For xs:string data types it is also possible to check if the field does not have content by using the field <i>with empty check</i>

This option is particulary useful when you have a mapping from an optional to a mandatory attribute.
 
With <b>Custom XPath</b> you can completly customize your if/else statements. You can use as an example the generated condition and modified according to your needs.


### 
Option <b>Constant</b> allows you to define a static value of a specific <i>output data type</i>.

With <b>Parameters</b> you can define a static value using one of the <i>parameters</i> defined in your transformation. A list of compatible parameters will appear based on your selected <i>output data type</i>

<b>XPath</b> option allows you add an XPath expression as default value. This could be handy if you would like to refer to another field or assign a more complex value as fallback value.

### 
If you enable the option <i> With empty check</i>  the condition will also check that the source attribute node has content. Note that this option is only available for <i> String</i> data types that accept empty content like <code>xs:string</code> or <code>xs:base64Binary</code>

#### Allows you to use a conditional test to determine which value should be set to the destination attribute
Allows you to use a conditional test to determine which value should be set to the destination attribute

Option <b>If exists</b> checks if the source attribute is present in the message or not. Depending on the evaluation of this condition, a different source value is mapped to the destination. If the source attribute is present in the message the source attribute defined in your rule will be used, otherwise the default value will be used. 

For xs:string data types it is also possible to check if the field does not have content by using the field <i>with empty check</i>

This option is particulary useful when you have a mapping from an optional to a mandatory attribute.
 
With <b>CustomXPath</b> you can completly customize your if/else statements. You can use as an example the generated condition and modified according to your needs.




### 
If this option is enabled,  you can create a xs:date/time constant with the current date/time information. 
Otherwise, you can enter a specific xs:date/time using the date, time and time zone fields accordingly.


### 
You can create an input with the value of one of the elements of the selected enumeration.

### 
In case you want to have an empty string as value, you can do it by using the <i>XPath</i> option and adding empty single quotes <code>''</code>. In this way it is clear that it is an intended user action and not a mistake.

