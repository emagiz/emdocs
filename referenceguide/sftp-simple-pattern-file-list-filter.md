# SFTP simple pattern file list filter
#### SFTP file filter that matches the name of the file against a simple ant-style pattern.
SFTP file filter that supports ant-style path expressions, which are less powerful but more readable than regular expressions.

This filter only filters on the name of the file, the rest of the path is ignored.

#### Pattern
Ant-style expression that describes a pattern for filtering files by their name. 

The ant style expression uses the following rules:
'?' - matches one character
'*' - matches zero or more characters

Some examples:
<code>t?st.xml</code> - matches <code>test.xml</code> but also <code>tast.xml</code> or code>txst.xml</code>
<code>*.xml</code> - matches all <code>.xml</code> files 

Note: Use a <i>regex pattern file list filter</i> for advanced patterns with regular expressions.

