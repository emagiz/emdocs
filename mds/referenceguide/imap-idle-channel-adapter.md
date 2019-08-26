---
id: imap-idle-channel-adapter
title: IMAP idle channel adapter
sidebar_label: IMAP idle channel adapter
---
#### Defines an event-driven IMAP mail receiving adapter. 
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/mail.html#mail-namespace" target="_blank">External documentation</a>

Use this adapter when your server supports IMAP IDLE. If not, use an <i>Mail Inbound Channel Adapter</i> instead.

It enables event-driven notifications, no poller is necessary for this adapter. 
It will send a Message to the specified channel as soon as it receives the notification that new mail is available.

Specifiy a <i>Task Executor</i> when new mail messages should be processed asynchronously.

#### Error channel
If a (synchronous) downstream exception is thrown and an error channel is specified, the <code>MessagingException</code> will be sent to this channel. Otherwise, any such exception will simply be logged as a warning by the channel adapter.

#### Should delete messages
Specify whether mail messages should be deleted after retrieval.

#### Should mark messages as read
Specify whether mail messages should be marked as read after being retrieved (not supported by all mail servers, e.g. POP3).

#### User flag
Specify the user flag to mark messages read by the adapter when the mail store does not support the RECENT flag but does support user flags (keywords). This flag is set regardless of the <i>should mark messages as read</i> attribute. It is used by the default search strategy to ignore already processed messages.

Default is <code>spring-integration-mail-adapter</code>.

#### Mail filter expression
Allows you to provide a SpEL expression which defines a fine grained filtering criteria for the mail messages to be processed by this adapter.

#### Max fetch size
Specify the maximum number of mail messages to fetch per receive call.	

#### Mail properties
Reference to a <i>Properties</i> entity that contains mail properties.

#### Store URI
The URI for the mail store. 

Typically looks like the following (the underlined words need to be replaced by the actual values):
<code>(pop3[s]|imap[s])://<u>user</u>:<u>password</u>@<u>host</u>[:<u>port</u>]/INBOX</code>

Note that you can use property placeholders within the URI, for example:
<code>imaps://${username}:${password}@imap.gmail.com/INBOX</code>

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: imap-idle-channel-adapter
title: IMAP idle channel adapter
sidebar_label: IMAP idle channel adapter
---
#### Defines an event-driven IMAP mail receiving adapter. 
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/mail.html#mail-namespace" target="_blank">Documentation</a>

Use this adapter when your server supports IMAP IDLE. If not, use an <i>Mail Inbound Channel Adapter</i> instead.

It enables event-driven notifications, no poller is necessary for this adapter. 
It will send a Message to the specified channel as soon as it receives the notification that new mail is available.

Specifiy a <i>Task Executor</i> when new mail messages should be processed asynchronously.

#### Error channel
If a (synchronous) downstream exception is thrown and an error channel is specified, the <code>MessagingException</code> will be sent to this channel. Otherwise, any such exception will simply be logged as a warning by the channel adapter.

#### Store URI
The URI for the mail store. 

Typically looks like the following (the underlined words need to be replaced by the actual values):
<code>(pop3[s]|imap[s])://<u>user</u>:<u>password</u>@<u>host</u>[:<u>port</u>]/INBOX</code>

Note that you can use property placeholders within the URI, for example:
<code>imaps://${username}:${password}@imap.gmail.com/INBOX</code>

#### Should delete messages
Specify whether mail messages should be deleted after retrieval.

#### Should mark messages as read
Specify whether mail messages should be marked as read after being retrieved (not supported by all mail servers, e.g. POP3).

#### User flag
Specify the user flag to mark messages read by the adapter when the mail store does not support the RECENT flag but does support user flags (keywords). This flag is set regardless of the <i>should mark messages as read</i> attribute. It is used by the default search strategy to ignore already processed messages.

Default is <code>spring-integration-mail-adapter</code>.

#### Mail filter expression
Allows you to provide a SpEL expression which defines a fine grained filtering criteria for the mail messages to be processed by this adapter.

#### Max fetch size
Specify the maximum number of mail messages to fetch per receive call.	

#### Mail properties
Reference to a <i>Properties</i> entity that contains mail properties.

#### Channel
Channel where the generated messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the messages.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

