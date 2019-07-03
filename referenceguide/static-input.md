---
id: static-input
title: Static Input
sidebar_label: Static Input
---
### 
You can create a static input with the content of one of the parameters defined in your transformation. Note that the list of parameters that you are able to select are only the ones compatible with the selected <i>output data type</i>.

For example if your selected <i>output data type</i> is <code>xs:nonEmptyString</code>, you will see parameters with data types like <code>xs:string</code> or <code>xs:integer</code>.

### 
Option <b>Constant</b> allows you to define a static value of a specific <i>output data type</i>.

With <b>Parameters</b> you can define a static value using one of the <i>parameters</i> defined in your transformation. A list of compatible parameters will appear based on your selected <i>output data type</i>

Selecting <b>Custom XPath</b> allows you to fully control the transformation of any value by entering your own custom XPath expression to handle the conversion. Technically, the XPath you enter will be used for the <code>&lt;xsl:value-of&gt;</code> statement in the generated stylesheet. Use the <i>view XSLT</i> button to see a preview how your XPath will be embedded in the resulting XSLT.

### 
In case you want to have an empty string as value, you can do it by adding empty single quotes <code>''</code>. In this way it is clear that it is an intended user action and not a mistake.

#### This operation provides different options to create an input that does not depend on any information from the source message
Operation with multiple options for creating an input that does not use information from the source message

Option <b>Constant</b> allows you to define a static value of a specific <i>output data type</i>.

With <b>Parameters</b> you can define a static value using one of the <i>parameters</i> defined in your transformation. A list of compatible parameters will appear based on your selected <i>output data type</i>

Selecting <b>Custom XPath</b> allows you to fully control the transformation of any value by entering your own custom XPath expression to handle the conversion. Technically, the XPath you enter will be used for the <code>&lt;xsl:value-of&gt;</code> statement in the generated stylesheet. Use the <i>view XSLT</i> button to see a preview how your XPath will be embedded in the resulting XSLT.

### 
If this option is enabled,  you can create a xs:date/time constant with the current date/time information. 
Otherwise, you can enter a specific xs:date/time using the date, time and time zone fields accordingly.


### 
You can create an input with the value of one of the elements of the selected enumeration.

### 
In case you want to have an empty string as value, you can do it by using the <i>XPath</i> option and adding empty single quotes <code>''</code>. In this way it is clear that it is an intended user action and not a mistake.

