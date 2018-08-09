# Mapping service gateway
#### Gateway that is called when any messaging component wants to do a mapping service lookup.
If any other messaging component (for example an <i>XSLT transformer</i>) needs to lookup a mapping, the request and reply messages go through this gateway. This decouples the components that use mappings from the actual mapping service implementation, and provides all normal messaging options and functionality for establishing the connection with this service.

This gateway also support <b>caching</b> by the Spring cache abstraction: if annotation-driven caching is enabled, the following caches must be accessible:
- <code>emagiz_mapping_cdmCodes</code>
- <code>emagiz_mapping_systemCodes</code>
- <code>emagiz_mapping_customAttributes</code>

To make it possible for any component to locate this gateway, it is registered as a singleton instance for the entire Java runtime instance this eMagiz configuration is running in. This has the following implications:
 - <i>Only <b>one instance</b> of this gateway may exist at any moment in a Java runtime instance.</i> This means that any eMagiz configuration can at most contain one mapping service gateway, and only one such configuration can be loaded at a time (per Java runtime instance).
 - <i>This gateway must be registered <b>before</b> any component tries to use the mapping service.</i> This means that in case of running multiple eMagiz configurations in a single Java runtime instance, the configuration with the mapping service gateway must be loaded before any configurations that try to use mappings.

#### Service interface
The name of the interface which will be exposed by this gateway.

#### Request timeout
The amount of time (in milliseconds) the dispatcher would wait to send a message. This timeout would only apply if there is a potential to block in the send call, for example if this gateway is hooked up to a queue channel.

#### Reply timeout
Allows you to specify how long this gateway will wait (in milliseconds) for the reply message before returning <code>null</code>.

By default it will wait indefinitely.

#### Error channel
The channel that error messages will be sent to if a failure occurs in this gateway's invocation.

If no <i>error channel</i> is provided (the default), this gateway will propagate exceptions to the caller.

To completely suppress exceptions, provide a reference to the <i>nullChannel</i> here.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Request channel
Channel where request messages should be sent to.

You can select the <code>nullChannel</code> here to silently drop the request messages.

<i>Required</i>

#### Reply channel
Channel to consume the reply messages from.

<i>Required</i>

