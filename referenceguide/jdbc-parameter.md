---
id: jdbc-parameter
title: JDBC parameter
sidebar_label: JDBC parameter
---
#### Name
The name of the parameter to be passed into the stored procedure or stored function. 

<i>Required</i>.

#### Value
The value of the parameter. You have to provide either this attribute or the expression attribute.

<i>Optional</i>.

#### Type
This attribute specifies the type of the value. If nothing is provided this attribute will default to <code>java.lang.String</code>. 

This attribute is only used when the value attribute is used. 

<i>Optional</i>.

#### Expression
Instead of the value attribute, you can also specify a SpEL expression for passing the value of the parameter. If you specify the expression the value attribute is not allowed. 

<i>Optional</i>.

