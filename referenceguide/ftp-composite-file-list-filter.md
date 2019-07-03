---
id: ftp-composite-file-list-filter
title: FTP composite file list filter
sidebar_label: FTP composite file list filter
---
#### Combines any number of FTP file list filters.
<a href="http://docs.spring.io/spring-integration/docs/2.2.6.RELEASE/reference/html/files.html#file-reading" target="_blank">Documentation</a>

A composite file list filter combines any number of file list filters. Only when all filters in the list accept a file, the composite file list filter will accept it.


Sub filters of this composite filter. A file must pass through each sub filter in order to be accepted by the main composite filter. The filters are applied in the specified order until a filter rejects the file or all filters have accepted the file.

<b>Accept once</b> - Ensures files are picked up only once from the directory. 
<b>Accept once per modification</b> - Passes files only one time per last modified time.
<b>Age</b> - Only accepts files with an age within the specified limits.
<b>Delay</b> - Delays the filtering process.
<b>Lock-file</b> - Accepts files only when there is no corresponding lock-file present.
<b>Regex pattern</b> - Matches the name of the file against a regular expression.
<b>Regular files only</b> - Only accepts regular files, not directories or symbolic links.
<b>Simple pattern</b> - Matches the name of the file against a simple ant-style pattern.
<b>Size</b> - Only accepts files with a size within the specified limits.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

