---
id: flat-file-to-xml-transformer
title: Flat file to XML transformer
sidebar_label: Flat file to XML transformer
---
#### Delete file after transformation
Specify whether to delete the File after a (successful) transformation. 

When set to true, it will only have an effect if the inbound message has a File payload or a FileHeaders.ORIGINAL_FILE header value containing either a File instance or a String representing the original file path.

Default is false.

#### Line mapper type
Sets the type of the used line mapper which maps lines to objects.

Required.

Options:
<b>1. Default line mapper</b>
Default used when all of the records in a file have the same format.
Converts and maps lines to domain objects.
<b>2. Pattern matching composite line mapper</b>
Used when there are multiple line types within a single input file. It selects the correct mapping for each line using pattern matching.


#### Line tokenizer type
Specifies the type of the used <i>Line Tokenizer</i>

Given line of input, a <i>Field Set</i> representing the line will be returned by the tokenizer. This <i>Field Set</i> can then be passed to a <i>Field Set Mapper</i>. 

<b>Delimited Line Tokenizer</b> - Used for files where fields in a record are separated by a delimiter. 
<b>Fixed Length Tokenizer</b> - Used for files where fields in a record are each a 'fixed width'. 

#### Result type
Sets the result type for the generated XML document.

Default when empty: "String".

#### Charset
Sets the character set used for reading the input data. 

Default is the default character set of this Java virtual machine.

#### Root element
Specifies the name that will be used for the root element in the resulting XML document. 

The name "flat-file" is used by default.

#### Record element
Specifies the name that will be used for the record elements in the resulting XML document. 

The name "record" is used by default.

#### Namespace
Specifies the namespace in which to create the resulting XML document. 

Default is 'empty', which indicates no namespace.

#### Lines to skip
The number of lines to skip at the start of a file. Can be used if the file contains a header without useful (column name) information, and without a comment delimiter at the beginning of the lines.

Default is '0'.

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

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

