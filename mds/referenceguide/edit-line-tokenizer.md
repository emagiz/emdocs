---
id: edit-line-tokenizer
title: Edit line tokenizer
sidebar_label: Edit line tokenizer
---
#### Line tokenizer type
Specifies the type of the used <i>Line Tokenizer</i>

Given line of input, a <i>Field Set</i> representing the line will be returned by the tokenizer. This <i>Field Set</i> can then be passed to a <i>Field Set Mapper</i>. 

<b>Delimited Line Tokenizer</b> - Used for files where fields in a record are separated by a delimiter. 
<b>Fixed Length Tokenizer</b> - Used for files where fields in a record are each a 'fixed width'. 

#### Delimiter
The delimiter character.

Default is a comma.

#### Strict
If true (the default) then number of tokens in line must match the number of tokens defined (by Range, columns, etc.) in LineTokenizer. If false then lines with less tokens will be tolerated and padded with empty columns, and lines with more tokens will simply be truncated.

Default is 'true'.

#### Included fields
The fields to include in the output by position (comma separated list of field numbers, starting at 0).

By default all fields are included, but this property can be set to pick out only a few fields from a larger set. Note that if field names are provided, their number must match the number of included fields.

