Small update that prevents specific issues that could occur when a flow did not correctly remove headers 'replyChannel' and/or 'errorChannel' from messages when needed.
## New features
- When serializing messages (i.e. when sending them to a JMS queue or storing them in the channel message store) headers 'replyChannel' and 'errorChannel' are now stripped from the message. Auto-generated eMagiz flows normally removed them already when needed, but it was easy to forget when manually building flows. This could cause problems, most notably when storing these messages in the H2 channel message store ("Message with id ‘(…)' was not deleted." warnings).
## Minor changes
- Updated bundle 'com.emagiz.components.jdbc' from 5.3.0 to 5.4.0
- Updated bundle 'com.emagiz.osgi.extender.jms' from 1.1.0 to 1.2.0
