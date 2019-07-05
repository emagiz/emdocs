# Security settings
#### Security settings that are applied on the address level.
Security settings which will be applied against any addresses with a name that matches a certain wildcard expression.

When <i>match</i> is <code>jms.queue.example</code> for example, the settings would only be applied to any addresses which exactly match the address <code>jms.queue.example</code>. You can also use wildcards to apply settings against many addresses. For example, if you used the match string <code>jms.queue.#</code>, the settings would be applied to all addresses that start with <code>jms.queue.</code> (which would be all JMS queues).

Note that only the most specific match is applied for each address. Some examples from most specific to least specific: <code>jms.queue.example</code> (matches one JMS queue), <code>jms.*.example</code> (matches one JMS queue and one JMS topic), <code>jms.queue.#</code> (matches all JMS queues), <code>jms.#</code> (matches all JMS queues and JMS topics).

#### Address match
A HornetQ wildcard expression contains words delimited by the character <code>.</code> (full stop).

The special characters <code>#</code> and <code>*</code> also have special meaning and can take the place of a word:
- the character <code>#</code> matches any sequence of zero or more words
- the character <code>*</code> matches a single word

So the wildcard <code>news.europe.#</code> would match <code>news.europe</code>, <code>news.europe.sport</code>, <code>news.europe.politics</code> and <code>news.europe.politics.regional</code>, but would not match <code>news.usa</code>, <code>news.usa.sport</code> nor <code>entertainment</code>.

The wildcard <code>news.*</code> would match <code>news.europe</code>, but not <code>news.europe.sport</code>.

The wildcard <code>news.*.sport</code> would match <code>news.europe.sport</code> and also <code>news.usa.sport</code>, but not <code>news.europe.politics</code>.

Note that addresses of JMS queues are always prefixed with <code>jms.queue.</code> and addresses of JMS topics with <code>jms.topic.</code>. So the wildcard <code>jms.queue.#</code> would match all JMS queues for example.

<i>Required</i>

#### Send
Comma-separated list of user roles that are granted permission to send a message to matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Consume
Comma-separated list of user roles that are granted permission to consume a message from a queue bound to matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Create durable queue
Comma-separated list of user roles that are granted permission to create a durable queue under matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Delete durable queue
Comma-separated list of user roles that are granted permission to delete a durable queue under matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Create non-durable queue
Comma-separated list of user roles that are granted permission to create a non-durable queue under matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Delete non-durable queue
Comma-separated list of user roles that are granted permission to delete a non-durable queue under matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Manage
Comma-separated list of user roles that are granted permission to invoke management operations by sending management messages to the management address.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

# Security settings
Artemis contains a flexible role-based security model for applying security to queues, based on their addresses. The security settings on this page will be applied against any address with a name that matches the <i>Address match</i> wildcard expression.

<a href="https://activemq.apache.org/artemis/docs/latest/security.html#role-based-security-for-addresses" target="_blank">Documentation</a>


Artemis contains a flexible role-based security model for applying security to queues, based on their addresses.

#### Address match
Artemis allows sets of permissions to be defined against the queues based on their address. 
Address expression contains words delimited by the character <code>.</code> (full stop).

The special characters <code>#</code> and <code>*</code> also have special meaning and can take the place of a word:
- the character <code>#</code> matches any sequence of zero or more words
- the character <code>*</code> matches a single word

So the wildcard <code>news.europe.#</code> would match <code>news.europe</code>, <code>news.europe.sport</code>, <code>news.europe.politics</code> and <code>news.europe.politics.regional</code>, but would not match <code>news.usa</code>, <code>news.usa.sport</code> nor <code>entertainment</code>.

The wildcard <code>news.*</code> would match <code>news.europe</code>, but not <code>news.europe.sport</code>.

The wildcard <code>news.*.sport</code> would match <code>news.europe.sport</code> and also <code>news.usa.sport</code>, but not <code>news.europe.politics</code>.

<i>Required</i>

#### Send
Comma-separated list of user roles that are granted permission to send a message to matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Consume
Comma-separated list of user roles that are granted permission to consume a message from a queue bound to matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.


#### Create durable queues
Comma-separated list of user roles that are granted permission to create a durable queue under matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Delete durable queues
Comma-separated list of user roles that are granted permission to delete a durable queue under matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Create non-durable queues
Comma-separated list of user roles that are granted permission to create a non-durable queue under matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Delete non-durable queues
Comma-separated list of user roles that are granted permission to delete a non-durable queue under matching addresses.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Manage
Comma-separated list of user roles that are granted permission to invoke management operations by sending management messages to the management address.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Browse
Comma-separated list of user roles that are granted permission to browse a queue bound to the matching address.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Create addresses
Comma-separated list of user roles that are granted permission to create an address.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

#### Delete addresses
Comma-separated list of user roles that are granted permission to delete an address.

Note that the <i>cluster user</i> of the HornetQ server always has full privileges, even without specifying any security settings.

