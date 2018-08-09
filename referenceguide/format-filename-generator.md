# Format filename generator
#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Format
Specifies the format for generating a file name.

The following tokens are replaced by the indicated values:

<code>*FILE_NAME*</code> : original file name (without the optional file extension), or the message ID when the original file name is unknown
<code>*FILE_EXT*</code> : original file extension (including the '.'; can be the empty string), or ".msg" when the original file name is unknown
<code>*MSG_SEQ_NR*</code> : sequence number of the message, or "1" if it hasn't one
<code>*MSG_SEQ_SIZE*</code> : sequence size of the message, or "1" if it hasn't one
<code>*MSG_TIME*</code> : timestamp of the message, or the current time if it hasn't one, formatted using the pattern specified by <i>time pattern</i>
<code>*CUR_TIME*</code> : the current time (at the moment of the file name generation), formatted using the pattern specified by <i>time pattern</i>

Default is <code>*MSG_TIME* *FILE_NAME* (*MSG_SEQ_NR* of *MSG_SEQ_SIZE*)*FILE_EXT*</code>.

#### Time pattern
Specifies the pattern to use for formatting a timestamp (when using <code>*MSG_TIME* </code> or <code>*CUR_TIME*</code>). The pattern must follow the <a href="http://joda-time.sourceforge.net/api-release/org/joda/time/format/DateTimeFormat.html" target="_blank">DateTimeFormat</a> syntax.

Default is <code>yyyy-MM-dd HH.mm.ss.SSS</code>.

