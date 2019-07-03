---
id: default-sftp-session-factory
title: Default SFTP session factory
sidebar_label: Default SFTP session factory
---
#### Session factory for creating connections with an SFTP server.
<a href="http://docs.spring.io/spring-integration/docs/2.2.6.RELEASE/reference/html/sftp.html#sftp-session-factory" target="_blank">Documentation</a>

Simple SFTP session factory that doesn't provide session caching/pooling, but creates a new session for every request.

When used by a <i>SFTP inbound channel adapter</i> this creates a new session + login attempt each time the adapter synchronizes the remote SFTP directory. When used by a <i>SFTP outbound channel adapter</i> this creates a new session + login attempt each time the adapter receives a message.

Note: SFTP = <b>SSH File Transfer Protocol</b>, an extension of the Secure Shell protocol (SSH) to provide secure file transfer capability. Not to be confused with "regular" FTP(S), which is a completely unrelated (and incompatible) file transfer protocol.

Please be aware that, depending on the SSH encryption level used by the server, you might need to install the <i>Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files</i> to successfully establish secure connections.

#### Timeout
The timeout property is used as the socket timeout parameter, as well as the default connection timeout.

Default is <code>0</code>, indicating that no timeout will occur.

#### Client version
Allows you to set the client version property.

The default depends on the underlying <i>JSch</i> version, but it will look like <code>SSH-2.0-JSCH-0.1.54</code>.

#### Host key alias
The host key alias, used when comparing the host key to the known hosts list. This is useful when multiple SSH servers with different host keys are located on the same host.

<i>Optional</i>

#### Server alive interval
The timeout interval (in milliseconds) before a server-alive message is sent, in case no message is received from the server.

#### Server alive count max
Specifies the number of server-alive messages, which will be sent without any reply from the server before disconnecting.

Default is <code>1</code>.

#### Enable daemon thread
If enabled all threads will be daemon threads, i.e. their running does not avoid a shutdown of the VM. If disabled normal non-deamon threads will be used (and the VM can only shutdown after disconnecting).

Default is <code>false</code>.


Allows you to specify additional (custom) configuration settings on the underlying <i>JSch</i> session.

<i>Optional</i>

#### Host
The host you want connect to.

<i>Required</i>

#### Port
The port over which the SFTP connection shall be established.

Default is <code>22</code>.

#### User
The remote user to use.

<i>Required</i>

#### Password
The password to authenticate against the remote host.

One of <i>password</i> or <i>private key</i> is required.

#### Private key
The location of the private key file used for authenticating against the remote host. Supported file formats include <i>OpenSSH</i> keys (<code>.pem</code>, <code>.key</code>, etc.) and <i>PuTTY</i> keys (<code>.ppk</code>).

Example: <code>resources/00-012345_my-key.pem</code>.

One of <i>password</i> or <i>private key</i> is required.

#### Private key passphrase
The password for the private key.

While it is not required to protect your key file with a password, it is highly recommended to do so.

<i>Optional</i>

#### Known hosts
Specifies the filename that will be used for a host key repository. The file has the same format as OpenSSH's <code>known_hosts</code> file.

<i>Required</i>, unless <i>allow unknown keys</i> is enabled.

#### Allow unknown keys
Set to <code>true</code> to unconditionally allow connecting to an unknown host or when a host's key has changed, or when a <i>known hosts</i> file is not available.

If you provide a (possibly empty) <i>known hosts</i> file <b>and</b> you enable <i>allow unknown keys</i>, the new key(s) will be added to the file automatically. You can use this to initially fill the <i>known hosts</i> file, after which you should deploy again with <i>allow unknown keys</i> disabled.

Note that allowing unknown keys makes the connection vulnerable to man-in-the-middle attacks.

Default is <code>false</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

