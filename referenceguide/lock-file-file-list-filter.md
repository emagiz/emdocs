# Lock-file file list filter
#### Accepts files only when there is no corresponding lock-file present.
File list filter that passes files only when there is no corresponding lock-file present. A file is recognized as a lock-file by (configurable) naming convention, e.g. having the suffix <code>.lock</code>. Lock-files are usually empty, but this is not a requirement. Lock-files themselves are never passed by this filter.

#### Lock-file regex
Regular expression describing the naming convention for lock-files. Any file with a name matching this regex will be considered a lock-file and will therefore never be passed by this filter.

This value may contain capturing groups (for use in the <i>lock-file target</i> setting) by putting parts of the regex within parentheses.

Default is <code>(.*)\\.lock</code>, i.e. a lock-file has the <code>.lock</code> suffix and the rest of the file name will be put into capturing group number 1.

#### Lock-file target
File name of the target file that is being locked by a lock-file. 

This value may contain references to capturing groups (from the <i>lock-file regex</i> setting) by using a dollar sign followed by the capturing group number. 

Default is <code>$1</code>, i.e. capturing group number 1 contains the full file name of the target file being locked by a lock-file.

