# Recursive leaf-only directory scanner
#### Directory scanner that lists all files inside a directory and subdirectories, without limit.
Directory scanner that lists all files inside a directory and subdirectories, without limit.

This scanner should not be used with directories that contain a vast number of files or on deep trees, as all the file names will be read into memory and the scanning will be done recursively.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Filter
A custom file filter to be used by this scanner.

Note that <b>all</b> filtering options on a <i>file inbound channel adapter</i> are completely ignored when using a custom directory scanner. In those cases you should provide the required filters on the scanner (i.e. here) instead.

