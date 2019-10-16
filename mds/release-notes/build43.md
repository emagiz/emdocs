Small update that prevents a potential performance issue related to the use of very large message headers.
## New features
- When (custom) message headers are mapped to JMS properties, headers with names longer than 256 characters or values longer than 1024 characters are now skipped. This should prevent performance problems caused by such large values, usually as a result of custom "temporary" message headers that were never properly cleaned up. Note that does not change how message headers work or how they can be used in message flows at all: the only theoretical difference that might be noticable in flows is when using JMS message selector expressions on rediculous large values.
- New support object 'no-op JMS header mapper' that does not map any message headers from or to JMS headers/properties. This component is primarily intended to be used by the auto-generated "bridge flows" in Artemis JMS server flows to ensure message headers are not inadvertently forwarded to eMagiz iPaaS.
## Minor changes
- Updated bundle 'com.emagiz.osgi.extender.jms' from 1.2.0 to 1.3.0
- Updated bundle 'com.emagiz.components.jms' from 5.0.1 to 5.1.0
