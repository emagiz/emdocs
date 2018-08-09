# Groovy variable
Allows you to define custom script variable bindings. This attribute isn't mutually exclusive with <i>variables</i> setting (see the <i>basic</i> tab) and all variables will be merged to one map.
<hr/>The variables <code>payload</code> and <code>headers</code> are always automatically available, even if you do not manually specify any variables. Since these two variables already give you access to all information in the message from your Groovy script, the main use-case for custom variables is probably to pass property values to the script.

#### Name
The variable name. Must be a valid Groovy identifier.

<i>Required</i>

#### Value
Value for this variable. This is a static value, but note that you can also use <code>${property}</code> notation here.

This value will be passed as a <code>String</code> to the Groovy script. If required, you can easily convert the data type using the Groovy <code>as</code> keyword. For example: <code>variableName as Integer</code>.

Either <i>value</i> or <i>ref</i> must have a value (but not both).

#### Ref
Value for this variable as a reference to any bean in this flow. This can be useful to pass a support object to the Groovy script, for example passing a <i>composite file list filter</i> if the Groovy script wants to re-use the file filtering functionality.

Either <i>value</i> or <i>ref</i> must have a value (but not both).

