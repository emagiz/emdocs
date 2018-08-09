
Used for preparing and sending MIME messages.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/mail.html#mail-outbound" target="_blank">Documentation</a>

Clients should talk to the mail sender through this interface if they need mail functionality beyond SimpleMailMessage. 

The recommended way of using this interface is the MimeMessagePreparator mechanism, possibly using a MimeMessageHelper for populating the message. See MimeMessageHelper's javadoc for an example.

The entire JavaMail Session management is abstracted by the JavaMailSender. Client code should not deal with a Session in any way, rather leave the entire JavaMail configuration and resource handling to the JavaMailSender implementation. This also increases testability.

A JavaMailSender client is not as easy to test as a plain MailSender client, but still straightforward compared to traditional JavaMail code: Just let createMimeMessage() return a plain MimeMessage created with a Session.getInstance(new Properties()) call, and check the passed-in messages in your mock implementations of the various send methods.


Id
Name that uniquely identifies this flow component.

<i>Required</i>


Host
Set the mail server host, typically an SMTP host.

Example:
<code>mail.examplehost.com</code>


Username
Set the username for the account at the mail host, if any.

Note that the mail session has to be configured with the property "mail.smtp.auth" set to true, else the specified username will not be sent to the mail server by the runtime.


Password
Set the password for the account at the mail host, if any.

Note that the mail session has to be configured with the property "mail.smtp.auth" set to true, else the specified password will not be sent to the mail server by the runtime.


Protocol
Set the mail protocol. 

Default is "smtp". 


Port
Set the mail server port.

Default is DEFAULT_PORT, letting JavaMail use the default SMTP port (25).


Default encoding
Set the default encoding to use for MimeMessages created by this instance.


Set JavaMail properties for the Session.

A new Session will be created with those properties.

Non-default properties in this instance will override given JavaMail properties.

