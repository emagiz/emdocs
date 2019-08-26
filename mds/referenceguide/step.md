---
id: step
title: Step
sidebar_label: Step
---

A Step is an independent, specific phase of a batch Job, such that every Job is composed of one or more Steps. 

Similar to a Job, a step has an individual <code>StepExecution</code> that represents a single attempt to execute a <i>Step</i>. StepExecution stores the information about current and exit statuses, start and end times, and so on, as well as references to its corresponding <i>Step</i> and <code>JobExecution</code> instances

The id attribute must be specified.


Strategy interface for providing the data.

Implementations are expected to be stateful and will be called multiple times for each batch, with each call to read() returning a different value and finally returning null when all input data is exhausted.

### _id
The rest template to use for sending HTTP requests.

If not specified the default rest template from the Spring Framework will be used (<i>org.springframework.web.client.RestTemplate</i>).

### _id
The rest template to use for sending HTTP requests.

If not specified the default rest template from the Spring Framework will be used (<i>org.springframework.web.client.RestTemplate</i>).


Simple ItemProcessor that does nothing - simply passes its argument through to the caller. Useful as a default when the reader and writer in a business process deal with items of the same type, and no transformations are required.



This entity is an item writer that writes items to Azure Event Hubs as events.

---
id: step
title: Step
sidebar_label: JDBC batch item writer
---

Item writer that uses the batching features from NamedParameterJdbcTemplate to execute a batch of statements for all items provided. You can use this support object as Item Writer in your <i>Jobs</i>.

The user must select at least a data source support object and provide column names and a table name or a complete SQL query. 
You can use either named parameters or the traditional indexed parameters by using the '?' placeholder. The parameter type selection has influence on the number of supported item types.

<a href="https://docs.spring.io/spring-batch/trunk/apidocs/org/springframework/batch/item/database/JdbcBatchItemWriter.html">External documentation</a>

### _id
Select a data source that provides the connections to the destination database.

<i>Required</i>

### _id
Select a data source that provides the connections to the destination database.

<i>Required</i>

### _id
Select the JDBC data source that provides the connections to the Amazon Redshift   database.

<i>Required</i>.

### _id
Select the JDBC data source that provides the connections to the Amazon Redshift   database.

<i>Required</i>.

### _id
Set the session factory

### _id
Set the session factory

---
id: step
title: Step
sidebar_label: Step
---
#### Resource
Input resource file for the reader. The resource can be created using  the <code>JobLaunchRequest</code> job parameters.

Example

<code>file:#{jobParameters['input.file']}</code>

Note that you need to set the <i>scope</i> to <i>Step</i>


#### Line mapper type
Sets the type of the used line mapper which maps lines to objects.

Required.

Options:
<b>1. Default line mapper</b>
Default used when all of the records in a file have the same format.
Converts and maps lines to domain objects.
<b>2. Pattern matching composite line mapper</b>
Used when there are multiple line types within a single input file. It selects the correct mapping for each line using pattern matching.
<b>3. Pass through line mapper</b>
Useful for passing the original String back directly rather than a mapped object.



#### Line tokenizer type
Specifies the type of the used <i>Line Tokenizer</i>

Given line of input, a <i>Field Set</i> representing the line will be returned by the tokenizer. This <i>Field Set</i> can then be passed to a <i>Field Set Mapper</i>. 

<b>Delimited Line Tokenizer</b> - Used for files where fields in a record are separated by a delimiter. 
<b>Fixed Length Tokenizer</b> - Used for files where fields in a record are each a 'fixed width'. 

#### Field set mapper type
Specifies the field set mapper type

Required.

Options:
<b>1. Xml field set mapper</b>
It converts a FieldSet to an XML document, by adding an XML element for each field to the XML root element. These XML elements will have the same name as the field they represent, and will have the same  field value as their (text) content. 

<b>2. Pass through field set mapper</b>
Useful for passing a FieldSet back directly rather than a mapped object.

#### Scope
Allows to do a late binding of references accessible from the StepContext using #{..} placeholders. Using this feature, bean properties can be pulled from the step or job execution context and the job parameters. 

 <bean id="..." class="..." scope="step">
        <property name="name" value="#{jobParameters[input]}" />
 </bean>

#### Lines to skip
The number of lines to skip at the start of a file. Can be used if the file contains a header without useful (column name) information, and without a comment delimiter at the beginning of the lines.

Default is '0'.

#### Charset
Sets the character set used for reading the input data. 

Default is the default character set of this Java virtual machine.

#### Comment prefix
Comment prefixes (seperated by commas). Can be used to ignore header lines as well by using e.g. the first couple of column names as a prefix.

Default is '#'.

#### Strict
In strict mode the reader will throw an exception if the input resource does not exist.

Default is 'true'.

#### Line separator policy
Used to determine where the line endings are and do things like continue over a line ending if inside a quoted string.

<b>Simple record separator policy (default)</b> - treats all lines as record endings.
<b>Default record separator policy</b> - treats all lines as record endings, as long as they do not have unterminated quotes, and do not end in a continuation marker.
<b> Suffix record separator policy</b> - looks for an exact match for a String at the end of a line (e.g. a semicolon).

#### Line suffix
Lines ending in this terminator String signal the end of a record.

#### Ignore whitespace
Flag to indicate that the decision to terminate a record should ignore whitespace at the end of the line.

#### Quote character
The quote character.

Defaults to double quote mark.

#### Continuation character
The continuation marker.

Defaults to back slash.

#### Delimiter
The delimiter character.

Default is a comma.

#### Strict
If true (the default) then number of tokens in line must match the number of tokens defined (by Range, columns, etc.) in LineTokenizer. If false then lines with less tokens will be tolerated and padded with empty columns, and lines with more tokens will simply be truncated.

Default is 'true'.

#### Include fields
The fields to include in the output by position (comma separated list of field numbers, starting at 0).

By default all fields are included, but this property can be set to pick out only a few fields from a larger set. Note that if field names are provided, their number must match the number of included fields.

---
id: step
title: Step
sidebar_label: Step
---

A Step is an independent, specific phase of a batch Job, such that every Job is composed of one or more Steps. 

Similar to a Job, a step has an individual <code>StepExecution</code> that represents a single attempt to execute a <i>Step</i>. StepExecution stores the information about current and exit statuses, start and end times, and so on, as well as references to its corresponding <i>Step</i> and <code>JobExecution</code> instances

The id attribute must be specified.


Strategy interface for providing the data.

Implementations are expected to be stateful and will be called multiple times for each batch, with each call to read() returning a different value and finally returning null when all input data is exhausted.

### _id
The rest template to use for sending HTTP requests.

If not specified the default rest template from the Spring Framework will be used (<i>org.springframework.web.client.RestTemplate</i>).

### _id
The rest template to use for sending HTTP requests.

If not specified the default rest template from the Spring Framework will be used (<i>org.springframework.web.client.RestTemplate</i>).


Simple ItemProcessor that does nothing - simply passes its argument through to the caller. Useful as a default when the reader and writer in a business process deal with items of the same type, and no transformations are required.



This entity is an item writer that writes items to Azure Event Hubs as events.

---
id: step
title: Step
sidebar_label: JDBC batch item writer
---

Item writer that uses the batching features from NamedParameterJdbcTemplate to execute a batch of statements for all items provided. You can use this support object as Item Writer in your <i>Jobs</i>.

The user must select at least a data source support object and provide column names and a table name or a complete SQL query. 
You can use either named parameters or the traditional indexed parameters by using the '?' placeholder. The parameter type selection has influence on the number of supported item types.

<a href="https://docs.spring.io/spring-batch/trunk/apidocs/org/springframework/batch/item/database/JdbcBatchItemWriter.html">documentation</a>

### _id
Select a data source that provides the connections to the destination database.

<i>Required</i>

### _id
Select a data source that provides the connections to the destination database.

<i>Required</i>

### _id
Select the JDBC data source that provides the connections to the Amazon Redshift   database.

<i>Required</i>.

### _id
Select the JDBC data source that provides the connections to the Amazon Redshift   database.

<i>Required</i>.

### _id
Set the session factory

### _id
Set the session factory

---
id: step
title: Step
sidebar_label: Step
---
#### Resource
Input resource file for the reader. The resource can be created using  the <code>JobLaunchRequest</code> job parameters.

Example

<code>file:#{jobParameters['input.file']}</code>

Note that you need to set the <i>scope</i> to <i>Step</i>


#### Line mapper type
Sets the type of the used line mapper which maps lines to objects.

Required.

Options:
<b>1. Default line mapper</b>
Default used when all of the records in a file have the same format.
Converts and maps lines to domain objects.
<b>2. Pattern matching composite line mapper</b>
Used when there are multiple line types within a single input file. It selects the correct mapping for each line using pattern matching.
<b>3. Pass through line mapper</b>
Useful for passing the original String back directly rather than a mapped object.



#### Line tokenizer type
Specifies the type of the used <i>Line Tokenizer</i>

Given line of input, a <i>Field Set</i> representing the line will be returned by the tokenizer. This <i>Field Set</i> can then be passed to a <i>Field Set Mapper</i>. 

<b>Delimited Line Tokenizer</b> - Used for files where fields in a record are separated by a delimiter. 
<b>Fixed Length Tokenizer</b> - Used for files where fields in a record are each a 'fixed width'. 

#### Field set mapper type
Specifies the field set mapper type

Required.

Options:
<b>1. Xml field set mapper</b>
It converts a FieldSet to an XML document, by adding an XML element for each field to the XML root element. These XML elements will have the same name as the field they represent, and will have the same  field value as their (text) content. 

<b>2. Pass through field set mapper</b>
Useful for passing a FieldSet back directly rather than a mapped object.

#### Scope
Allows to do a late binding of references accessible from the StepContext using #{..} placeholders. Using this feature, bean properties can be pulled from the step or job execution context and the job parameters. 

 <bean id="..." class="..." scope="step">
        <property name="name" value="#{jobParameters[input]}" />
 </bean>

#### Lines to skip
The number of lines to skip at the start of a file. Can be used if the file contains a header without useful (column name) information, and without a comment delimiter at the beginning of the lines.

Default is '0'.

#### Charset
Sets the character set used for reading the input data. 

Default is the default character set of this Java virtual machine.

#### Comment prefix
Comment prefixes (seperated by commas). Can be used to ignore header lines as well by using e.g. the first couple of column names as a prefix.

Default is '#'.

#### Strict
In strict mode the reader will throw an exception if the input resource does not exist.

Default is 'true'.

#### Line separator policy
Used to determine where the line endings are and do things like continue over a line ending if inside a quoted string.

<b>Simple record separator policy (default)</b> - treats all lines as record endings.
<b>Default record separator policy</b> - treats all lines as record endings, as long as they do not have unterminated quotes, and do not end in a continuation marker.
<b> Suffix record separator policy</b> - looks for an exact match for a String at the end of a line (e.g. a semicolon).

#### Line suffix
Lines ending in this terminator String signal the end of a record.

#### Ignore whitespace
Flag to indicate that the decision to terminate a record should ignore whitespace at the end of the line.

#### Quote character
The quote character.

Defaults to double quote mark.

#### Continuation character
The continuation marker.

Defaults to back slash.

#### Delimiter
The delimiter character.

Default is a comma.

#### Strict
If true (the default) then number of tokens in line must match the number of tokens defined (by Range, columns, etc.) in LineTokenizer. If false then lines with less tokens will be tolerated and padded with empty columns, and lines with more tokens will simply be truncated.

Default is 'true'.

#### Include fields
The fields to include in the output by position (comma separated list of field numbers, starting at 0).

By default all fields are included, but this property can be set to pick out only a few fields from a larger set. Note that if field names are provided, their number must match the number of included fields.

