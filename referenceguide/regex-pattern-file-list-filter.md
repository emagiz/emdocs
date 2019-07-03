---
id: regex-pattern-file-list-filter
title: Regex pattern file list filter
sidebar_label: Regex pattern file list filter
---
#### File filter that matches the name of the file against a regular expression.
File filter that matches the name of the file against a pattern that is described by a regular expression.

See the java documentation about patterns:
<a href="http://java.sun.com/javase/6/docs/api/java/util/regex/Pattern.html" target="_blank">Pattern documentation</a>

#### Pattern
A regular expression that describes the pattern for matching the file names.

Examples:
<code> ^.*\.xml$</code> - matches all <code> .xml</code> files
<code> ^test\d{4}\.xml$</code> - matches all filenames that start with <code>test</code> followed by 4 digits and end with <code> .xml</code>
 
See the Java documentation about patterns:
<a href="http://java.sun.com/javase/6/docs/api/java/util/regex/Pattern.html" target="_blank">Pattern documentation</a>

