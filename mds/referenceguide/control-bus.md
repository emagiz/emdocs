---
id: control-bus
title: Control bus
sidebar_label: Control bus
---
#### Service activator for managing components within the messaging framework.
<a href="https://docs.spring.io/spring-integration/docs/4.3.x/reference/html/system-management-chapter.html#control-bus" target="_blank">External documentation</a>

The control bus is a service activator for managing components within the messaging framework itself. It receives command messages on its <i>input channel</i> in the form of SpEL expressions, which are then executed in the application context.

If the executed command returns a result, this is send as the contents of a new message (or multiple messages) to the <i>output channel</i>. If the command does not return anything (or no <i>output channel</i> is configured), the command bus doesn't generate any output messages (it basically behaves like an <i>outbound channel adapter</i> in this case).

While any valid SpEL expression can be executed (for example <code>#headers.timestamp</code>, which will return the timestamp of the command message), the intended use is to call managed operations or lifecycle methods of specific messaging components. For example, the expression <code>@myInboundAdapter.stop()</code> will cause the <i>inbound channel adapter</i> with ID <code>myInboundAdapter</code> to stop (i.e, it will stop producing messages). See the documentation for all supported operations.

#### Output channel
Output channel where any results of the execution of the command message are send to. If not configured, the control bus will not generate any output.

If this property is set and the executed command returns a non-<code>null</code> result, this result object (or multiple result objects) is send as the payload of a message (or multiple messages) to the specified channel.

<i>Optional</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: control-bus
title: Control bus
sidebar_label: Control bus
---
#### Service activator for managing components within the messaging framework.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/system-management-chapter.html#control-bus" target="_blank">Documentation</a>

The control bus is a service activator for managing components within the messaging framework itself. It receives command messages on its <i>input channel</i> in the form of SpEL expressions, which are then executed in the application context.

If the executed command returns a result, this is send as the contents of a new message (or multiple messages) to the <i>output channel</i>. If the command does not return anything (or no <i>output channel</i> is configured), the command bus doesn't generate any output messages (it basically behaves like an <i>outbound channel adapter</i> in this case).

While any valid SpEL expression can be executed (for example <code>#headers.timestamp</code>, which will return the timestamp of the command message), the intended use is to call managed operations or lifecycle methods of specific messaging components. For example, the expression <code>@myInboundAdapter.stop()</code> will cause the <i>inbound channel adapter</i> with ID <code>myInboundAdapter</code> to stop (i.e, it will stop producing messages). See the documentation for all supported operations.

#### Output channel
Output channel where any results of the execution of the command message are send to. If not configured, the control bus will not generate any output.

If this property is set and the executed command returns a non-<code>null</code> result, this result object (or multiple result objects) is send as the payload of a message (or multiple messages) to the specified channel.

<i>Optional</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

