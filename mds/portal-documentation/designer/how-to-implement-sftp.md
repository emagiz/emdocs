# How 2 implement SFTP

https://my.emagiz.com/link/documentation/118  
**In the secured tunnels release we extend our support for file transfer patterns with SFTP. eMagiz already supported FTP and FTPS. So what’s new and different?**

 

**FTPS vs. SFTP**

Alexander Willemsen already mentioned the differences of FTPS and SFTP as an answer to a community question.

FTPS is the combination of FTP and SSL. Also known as the secure version of 'normal' FTP, just like HTTPS is the secure version of HTTP (both use SSL encryption). SFTP uses the SSH File Transfer Protocol. This extension of the Secure Shell protocol (SSH) provides secure file transfer capability. 

Except that FTPS and SFTP both handle file transfers and happen to contain the letters 'FTP' in their names, these protocols share nothing in common and are completely incompatible.

 

**New flow designer components**

Where can I find them? Just type in “sftp” in the search bar of the flow designer and you can start implementing SFTP for your integration projects.

The SFTP inbound channel adapter synchronizes a remote SFTP directory with a local directory and creates file-messages.

 

The SFTP inbound channel adapter has two tasks:

  - Communicate with a remote server in order to transfer files from a remote directory to a local directory;
  - For each transferred file, generate a message with that file as the payload and send it to the channel.
 

If your local directory already has one or more files it will first generate messages from those, and only when all local files have been processed, it will initiate the remote communication to retrieve more files.

 

The SFTP outbound channel adapter sends messages securely to a remote directory using the SSH File Transfer Protocol. It connects to the SFTP server and initiates an SFTP transfer for every file it receives in the payload of incoming messages.

 

The SFTP outbound channel adapter supports the following payloads:

  - java.io.File - the actual file object
  - byte[] - a byte array that represents the file contents
  - java.lang.String - text that represents the file contents
 

**New support objects**

The new inbound- and outbound channel adapters are accompanied with 3 new support objects:

 

  - Default SFTP session factory
  - Default SFTP caching session factory
  - Composite file list filter
 

To make the SFTP channel adapter work, a simple SFTP session factory can be applied for cases that don't require session caching/pooling. It creates a new session for every request. The SFTP caching session factory provides session caching/pooling, re-using existing sessions for multiple request. A composite file list filter combines any number of file list filters. Only when all filters in the list accept a file, the composite file list filter will accept it. For more details and implementation details, we refer to the helptexts included for each component.
