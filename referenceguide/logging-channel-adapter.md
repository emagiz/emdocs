# Logging channel adapter
#### Logs messages.
Use for debugging purposes.

#### Log full message
Specify whether to log the full message.

This attribute and the <i>expression</i> attribute are mutually exclusive.

Setting this to <code>true</code> is equivalent to setting an expression value of <code>#root</code> since the message is the root object against which the expression will be evaluated. If no <i>expression</i> is provided, and this value is <code>false</code> (the default), only the payload will be logged.

#### Expression
Provide a SpEL expression to be evaluated against the message as the root object. The evaluation result will be the information written to the log.

For example, the default behavior is equivalent to an expression of <code>payload</code>, or an expression may evaluate against the payload itself (<code>payload.address.city</code>) or headers (<code>headers.foo</code>).

This attribute and the <i>log full message</i> attribute are mutually exclusive. See the documentation on the <i>log full message</i> attribute for more information.

#### Level
Specifies the log level. 

Default : info

#### Logger name
Provide a name for the logger. This is useful when there are multiple <i>logging channel adapters</i> configured, and you would like to differentiate them within the actual log.

By default the logger name will be the fully qualified class name of the <code>LoggingHandler</code> implementation.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Channel
Channel to consume messages from.

<i>Required</i>

