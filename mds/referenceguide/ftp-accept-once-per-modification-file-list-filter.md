---
id: ftp-accept-once-per-modification-file-list-filter
title: FTP accept once per modification file list filter
sidebar_label: FTP accept once per modification file list filter
---
#### FTP file filter that passes files only one time per last modified time.
FTP file filter that passes files only one time per last modified time or when the internal buffer overflows and the file falls out.

The internal buffer uses FIFO order; newly accepted files are inserted at the back of the queue and eventually fall out when the queue overflows. When a file is accepted again due to a changed <i>last modified time</i>, it is removed from its position in the queue and inserted at the back.

Files with a <i>last modified time</i> less than threshold milliseconds old are not accepted. By default this threshold is set to 0, which causes any new file or files with a changed last modified time to be accepted.

#### File age threshold
Specifies the threshold for accepting files: files with a last modified time less than threshold milliseconds old will not be accepted by this filter.

Default is <code>0</code> (no threshold).

#### Max buffer size
Maximum size of the internal buffer before files will fall out.

Default is <i>10000</i>.

