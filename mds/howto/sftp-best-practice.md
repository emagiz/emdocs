# Best practices for using SFTP

## Which session factory do I need?

When occasionally retrieving or writing files to SFTP, use the *Default SFTP session factory*. When you use the *Default SFTP session factory* for every message/file a new connection will be set up. On some SFTP servers this might take up to seconds for each login, which might have impact on the performance of your flow.

When you need better performance (say writing multiple files in a minute, or retrieving files every minute) use the *Default SFTP **caching** session factory*. The *Default SFTP **caching** session factory* shares SFTP sessions for messages in your flow.

## Do I have to set up a retry mechanism?

When writing files to SFTP it is advisable to set a retry mechanism. Find the advanced tab on your *SFTP outbound channel adapter*. Under *Request handler advice chain* add a *Retry Advice*.

## Do I have to disable *Use temporary file name*?

This is no longer necessary. There was a bug on the SFTP servers of eMagiz Services, but this bug has been fixed. The best practice is to keep *Use temporary file name* property turned on.

## I get a *Failed to list files / items* or a *Failed to obtain pooled item*. What can I do?

This can be caused by incorrect connection settings. Check whether the correct properties have been set and whether the runtime has retrieved the latest properties.

## I get a *Failed to list files / items*, a *Pipe closed* or an *input stream is closed*. What can I do?

These notifications can be caused by a closed SFTP session due to inactivity. On the *Default SFTP **caching** session factory*, always set the *Server alive interval* property to 30000 (ms). This is also the default on new *Default SFTP **caching** session factory* components.

## I get a *Failed to write to*. What can I do.

Maybe the target folder does not exist and *Auto create directory* is off. It is also possible that the connection settings are incorrect. Check whether the correct properties have been set and whether the runtime has retrieved the latest properties.

## I often get 'Disconnecting from sftp.example.com port 22' and then a 'Caught an exception, leaving main loop due to Socket closed' warnings.

This can be caused by too many connections to the same server at the same time. If you have many flows connecting to the same SFTP server, make sure that the crons do not all trigger at the same time. 

## I get a ‘Failed to create FTPClient’

SFTP, FTP and FTPS are three different remote file transfer protocols with their own *session factory* components in the eMagiz flow designer. Make sure you use the one that corresponds to the server's protocol.

## One of my remote files is not picked up from the SFTP server (without any warning)

The default local filter is *AcceptOnceFileListFilter*. This can be replaced by your own file list filter on the advanced tab of the *SFTP inbound channel adapter*.

If every day you retrieve a file with the same filename and the *Delete remote files* property is set, it is advised to use a different local filename. You can add the current timestamp for example.