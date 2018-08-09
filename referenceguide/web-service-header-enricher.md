# Web service header enricher
#### Enriches the header of messages by adding a SOAP Action value.
<a href="http://docs.spring.io/spring-integration/docs/2.1.x/reference/html/messaging-transformation-chapter.html#header-enricher" target="_blank">Documentation</a>

Header enricher for adding web service specific message headers.

These headers can be used by any downstream web service outbound gateways. For example, adding a <i>SOAP action</i> header influences the SOAP action that will be used when calling the web service.

#### Output channel
Channel where output messages should be sent after (successfully) processing the input message.

You can select the <code>nullChannel</code> here to silently drop the output messages.

<i>Required</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Input channel
Channel to consume the input messages from.

<i>Required</i>

