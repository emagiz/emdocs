# Reference guide - flow components by category
> Jump to: [Data pipelines](#data-pipelines) | [File](#file) | [FTP(S)](#ftps) | [HTTP/REST](#httprest) | [JDBC](#jdbc) | [JMS/AMQP](#jmsamqp) | [Kafka](#kafka) | [Mail](#mail) | [Scripting](#scripting) | [SFTP](#sftp) | [TCP](#tcp) | [Web services](#web-services) | [XML](#xml) | [XMPP](#xmpp)

This page lists all components available in the flow designer grouped by *category* (HTTP/REST, web services, EDI, etc). The same list but grouped by *type* (transformer, filter, router, etc) is available [here](index.md).

A component with ~~strikethrough~~ indicates it is deprecated: hover to see the recommended alternative. Some components in the flow designer have additional settings that are (usually) accessed through new/edit/delete buttons: these "nested" components are listed as sub-items of the relevant component in the list below.

## Data pipelines
- Default execution context serializer
- Job
- Job execution listener gateway
- Job launching outbound gateway
- Job manager
- Job registry bean post processor
- Job repository
- Map job registry
- Simple job launcher
- Step execution listener gateway

## File
- [Composite file list filter](composite-file-list-filter.md)
  - [Accept once file list filter](accept-once-file-list-filter.md)
  - [Accept once per modification file list filter](accept-once-per-modification-file-list-filter.md)
  - [Age file list filter](age-file-list-filter.md)
  - [Delaying file list filter](delaying-file-list-filter.md)
  - [Lock-file file list filter](lock-file-file-list-filter.md)
  - [Regex pattern file list filter](regex-pattern-file-list-filter.md)
  - Regular files only file list filter
  - [Simple pattern file list filter](simple-pattern-file-list-filter.md)
  - [Size file list filter](size-file-list-filter.md)
- [File inbound channel adapter](file-inbound-channel-adapter.md)
- File item reader message source
- [File outbound channel adapter](file-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [File to bytes transformer](file-to-bytes-transformer.md)
- [File to string transformer](file-to-string-transformer.md)
- [Format file name generator](format-filename-generator.md)
- [Timestamped file name generator](timestamped-filename-generator.md)

## FTP(S)
- [Default FTP caching session factory](default-ftp-caching-session-factory.md)
- [Default FTP session factory](default-ftp-session-factory.md)
- [Default FTPS caching session factory](default-ftps-caching-session-factory.md)
- [Default FTPS session factory](default-ftps-session-factory.md)
- [File to bytes transformer](file-to-bytes-transformer.md)
- [File to string transformer](file-to-string-transformer.md)
- [Format file name generator](format-filename-generator.md)
- [FTP composite file list filter](ftp-composite-file-list-filter.md)
  - [Accept once file list filter](accept-once-file-list-filter.md)
  - [Delaying file list filter](delaying-file-list-filter.md)
  - [FTP accept once per modification file list filter](ftp-accept-once-per-modification-file-list-filter.md)
  - [FTP age file list filter](ftp-age-file-list-filter.md)
  - [FTP lock-file file list filter](ftp-lock-file-file-list-filter.md)
  - [FTP regex pattern file list filter](ftp-regex-pattern-file-list-filter.md)
  - FTP regular files only file list filter
  - [FTP simple pattern file list filter](ftp-simple-pattern-file-list-filter.md)
  - [FTP size file list filter](ftp-size-file-list-filter.md)
- [FTP inbound channel adapter](ftp-inbound-channel-adapter.md)
- [FTP outbound channel adapter](ftp-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [Timestamped file name generator](timestamped-filename-generator.md)

## HTTP/REST
- [Default HTTP header mapper](default-http-header-mapper.md)
- [HTTP inbound channel adapter](http-inbound-channel-adapter.md)
  - [HTTP header](http-header.md)
- [HTTP inbound gateway](http-inbound-gateway.md)
  - [HTTP header](http-header.md)
- [HTTP outbound channel adapter](http-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [HTTP URI variable](http-uri-variable.md)
  - OAuth 2.0 access token advice
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [HTTP outbound gateway](http-outbound-gateway.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [HTTP URI variable](http-uri-variable.md)
  - OAuth 2.0 access token advice
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [HTTP parameter map to XML transformer](parameter-map-to-xml-transformer.md)
- Jetty server
- OAuth 2.0 resource
- OAuth 2.0 REST template
- [REST template](rest-template.md)
  - [Amazon S3 authentication interceptor](amazon-s3-authentication-interceptor.md)
  - [Azure Storage Services authentication interceptor](azure-storage-services-authentication-interceptor.md)
  - [Basic access authentication interceptor](basic-access-authentication-interceptor.md)
- XSLT view

## JDBC
- [JDBC BoneCP data source](jdbc-bonecp-data-source.md)
- [JDBC channel message store](jdbc-channel-message-store.md)
- [JDBC data source transaction manager](data-source-transaction-manager.md)
- JDBC H2 connection pool
- [JDBC inbound channel adapter](jdbc-inbound-channel-adapter.md)
- [JDBC initialize database](jdbc-initialize-database.md)
  - [SQL script](sql-script.md)
- [JDBC OSGi data source reference](jdbc-osgi-data-source-reference.md)
- [JDBC outbound channel adapter](jdbc-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [JDBC outbound gateway](jdbc-outbound-gateway.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [JDBC result set to XML transformer](jdbc-result-set-to-xml-transformer.md)
- [JDBC stored procedure inbound channel adapter](jdbc-stored-procedure-inbound-channel-adapter.md)
  - [JDBC parameter](jdbc-parameter.md)
  - [JDBC SQL parameter definition](jdbc-sql-parameter-definition.md)
- [JDBC stored procedure outbound channel adapter](jdbc-stored-procedure-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [JDBC parameter](jdbc-parameter.md)
  - [JDBC SQL parameter definition](jdbc-sql-parameter-definition.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [JDBC stored procedure outbound gateway](jdbc-stored-procedure-outbound-gateway.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [JDBC parameter](jdbc-parameter.md)
  - [JDBC SQL parameter definition](jdbc-sql-parameter-definition.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)

## JMS/AMQP
- [ActiveMQ security manager gateway](activemq-security-manager-gateway.md)
- [Apache ActiveMQ Artemis server](apache-activemq-artemis-server.md)
  - [Address settings](address-settings.md)
  - [Cluster connection](cluster-connection.md)
  - [In-VM acceptor](in-vm-acceptor.md)
  - [In-VM connector](in-vm-connector.md)
  - [Netty acceptor](netty-acceptor.md)
  - [Netty connector](netty-connector.md)
  - [Security settings](security-settings.md)
- ~~[HornetQ caching connection factory](hornetq-caching-connection-factory.md "Deprecated: use JMS caching connection factory")~~
- ~~[HornetQ connection factory](hornetq-connection-factory.md "Deprecated: use Qpid JMS connection factory")~~
- ~~[HornetQ JMS server manager](hornetq-jms-server-manager.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[Address settings](address-settings.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[Bridge configuration](bridge-configuration.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[Cluster connection configuration](cluster-connection-configuration.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[Connector transport configuration](connector-transport-configuration.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[In-VM acceptor transport configuration](in-vm-acceptor-transport-configuration.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[In-VM connector transport configuration](in-vm-connector-transport-configuration.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[JMS queue configuration](jms-queue-configuration.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[Netty acceptor transport configuration](netty-acceptor-transport-configuration.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[Netty connector transport configuration](netty-connector-transport-configuration.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[Security settings](security-settings.md "Deprecated: use Apache ActiveMQ Artemis server")~~
  - ~~[Topic configuration](topic-configuration.md "Deprecated: use Apache ActiveMQ Artemis server")~~
- ~~[HornetQ security manager gateway](hornetq-security-manager-gateway.md "Deprecated: use ActiveMQ security manager gateway")~~
- [JMS caching connection factory](jms-caching-connection-factory.md)
- [JMS inbound channel adapter](jms-inbound-channel-adapter.md)
- [JMS inbound gateway](jms-inbound-gateway.md)
- [JMS listener container](jms-listener-container.md)
  - [JMS listener](jms-listener.md)
- [JMS message driven channel adapter](jms-message-driven-channel-adapter.md)
- JMS OSGi connection factory reference
- [JMS outbound channel adapter](jms-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [JMS outbound gateway](jms-outbound-gateway.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [JMS XML message converter](jms-xml-message-converter.md)
- [Qpid JMS connection factory](qpid-jms-connection-factory.md)
  - [AMQP connector settings](qpid-amqp-connector-setting.md)
- ~~[Sonic caching connection factory](sonic-caching-connection-factory.md "Deprecated: use JMS caching connection factory")~~
- [Sonic connection factory](sonic-connection-factory.md)
- ~~[WebSphere caching connection factory](websphere-caching-connection-factory.md "Deprecated: use JMS caching connection factory")~~
- [WebSphere connection factory](websphere-connection-factory.md)

## Kafka
- Kafka message driven channel adapter
- Kafka message listener container
- Kafka outbound channel adapter
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- Kafka template

## Mail
- [IMAP idle channel adapter](imap-idle-channel-adapter.md)
- [Java mail sender](java-mail-sender.md)
- [Mail attachment transformer](mail-attachment-transformer.md)
- [Mail header enricher](mail-header-enricher.md)
  - [Attachment filename](mail-header-enricher---attachment-filename.md)
  - [Bcc](mail-header-enricher---bcc.md)
  - [Cc](mail-header-enricher---cc.md)
  - [Content type](mail-header-enricher---content-type.md)
  - [From](mail-header-enricher---from.md)
  - [Multipart mode](mail-header-enricher---multipart-mode.md)
  - [Reply to](mail-header-enricher---reply-to.md)
  - [Subject](mail-header-enricher---subject.md)
  - [To](mail-header-enricher---to.md)
- [Mail inbound channel adapter](mail-inbound-channel-adapter.md)
- [Mail outbound channel adapter](mail-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [Mail to string transformer](mail-to-string-transformer.md)
- [MIME message to XML transformer](mime-message-to-xml-transformer.md)
- [MIME to S/MIME transformer](mime-to-s-mime-transformer.md)
- [S/MIME to MIME transformer](s-mime-to-mime-transformer.md)
- [XML to MIME message transformer](xml-to-mime-message-transformer.md)

## Scripting
- [Standard filter](standard-filter.md)
  - [Groovy variable](groovy-variable.md)
- [Standard header enricher](standard-header-enricher.md)
  - [Correlation id](standard-header-enricher---correlation-id.md)
  - [Custom header](standard-header-enricher---custom-header.md)
  - [Error channel](standard-header-enricher---error-channel.md)
  - [Expiration date](standard-header-enricher---expiration-date.md)
  - [Priority](standard-header-enricher---priority.md)
  - [Reply channel](standard-header-enricher---reply-channel.md)
- [Standard inbound channel adapter](standard-inbound-channel-adapter.md)
- [Standard router](standard-router.md)
  - [Groovy variable](groovy-variable.md)
  - [Value mapping](value-mapping.md)
- [Standard service activator](standard-service-activator.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Groovy variable](groovy-variable.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [Standard splitter](standard-splitter.md)
  - [Groovy variable](groovy-variable.md)
- [Standard transformer](standard-transformer.md)
  - [Groovy variable](groovy-variable.md)

## SFTP
- [Default SFTP caching session factory](default-sftp-caching-session-factory.md)
- [Default SFTP session factory](default-sftp-session-factory.md)
- [File to bytes transformer](file-to-bytes-transformer.md)
- [File to string transformer](file-to-string-transformer.md)
- [Format file name generator](format-filename-generator.md)
- [SFTP composite file list filter](sftp-composite-file-list-filter.md)
  - [Accept once file list filter](accept-once-file-list-filter.md)
  - [Delaying file list filter](delaying-file-list-filter.md)
  - [SFTP accept once per modification file list filter](sftp-accept-once-per-modification-file-list-filter.md)
  - [SFTP age file list filter](sftp-age-file-list-filter.md)
  - [SFTP lock-file file list filter](sftp-lock-file-file-list-filter.md)
  - [SFTP regex pattern file list filter](sftp-regex-pattern-file-list-filter.md)
  - SFTP regular files only file list filter
  - [SFTP simple pattern file list filter](sftp-simple-pattern-file-list-filter.md)
  - [SFTP size file list filter](sftp-size-file-list-filter.md)
- [SFTP inbound channel adapter](sftp-inbound-channel-adapter.md)
- [SFTP outbound channel adapter](sftp-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [Timestamped file name generator](timestamped-filename-generator.md)

## TCP
- [Byte array CR/LF (de)serializer](byte-array-cr-lf--de-serializer.md)
- [Byte array length header (de)serializer](byte-array-length-header--de-serializer.md)
- [Byte array raw (de)serializer](byte-array-raw--de-serializer.md)
- [Byte array single terminator (de)serializer](byte-array-single-terminator--de-serializer.md)
- [Byte array STX/ETX (de)serializer](byte-array-stx-etx--de-serializer.md)
- [Byte array text length header (de)serializer](byte-array-text-length-header--de-serializer.md)
- [Default TCP SSL context support](default-tcp-ssl-context-support.md)
- ISO8583 bytes to XML transformer
- ISO8583 XML to bytes transformer
- [TCP connection factory](tcp-connection-factory.md)
- [TCP inbound channel adapter](tcp-inbound-channel-adapter.md)
- [TCP inbound gateway](tcp-inbound-gateway.md)
- [TCP outbound channel adapter](tcp-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [TCP outbound gateway](tcp-outbound-gateway.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)

## Web services
- Complex SOAP header mapper
  - [SOAP to message header mapping](soap-to-message-header-mapping.md)
- Default WSDL 1.1 definition
- Detailed SOAP fault message resolver
- HTTP Components message sender
- Jetty server
- Mendix authentication SAAJ SOAP interceptor
- [Mendix authentication SOAP header mapper](mendix-authentication-soap-header-mapper.md)
- Merlin crypto
- Metacom authentication SAAJ SOAP interceptor
- Proxy web service message sender
- SAAJ SOAP message factory
- Simple XSD schema
- Simple WSDL 1.1 definition
- SOAP action callback
- [SOAP attachments header mapper](soap-attachments-header-mapper.md)
- SOAP fault message resolver
- SOAP message dispatcher
- SSL web service message sender
- [Web service header enricher](web-service-header-enricher.md)
  - [SOAP action](web-service-header-enricher---soap-action.md)
- [Web service inbound gateway](web-service-inbound-gateway.md)
- Web service message listener
- [Web service outbound gateway](web-service-outbound-gateway.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
  - [Web service URI variable](web-service-uri-variable.md)
- WS-Addressing action callback
- WSS4J security interceptor
- Zimbra authentication SAAJ SOAP interceptor

## XML
- [String to wrapped XML transformer](string-to-wrapped-xml-transformer.md)
- [FOP XSL-FO result factory](fop-xsl-fo-result-factory.md)
- [FOP XSL-FO result transformer](fop-xsl-fo-result-transformer.md)
- [Mapping service gateway](mapping-service-gateway.md)
- [Result to document transformer](result-to-document-transformer.md)
- [Result to string transformer](result-to-string-transformer.md)
- [XML to string transformer](xml-to-string-transformer.md)
- [XML validating filter](xml-validating-filter.md)
- [XPath expression](xpath-expression.md)
- [XPath filter](xpath-filter.md)
- [XPath header enricher](xpath-header-enricher.md)
  - [Header](xpath-header-enricher---header.md)
- [XPath router](xpath-router.md)
  - [XPath value mapping](xpath-value-mapping.md)
- [XPath splitter](xpath-splitter.md)
- [XPath transformer](xpath-transformer.md)
- [XSLT extension gateway](xslt-extension-gateway.md)
- [XSLT transformer](xslt-transformer.md)
  - [XSLT parameter](xslt-parameter.md)

## XMPP
- [XMPP connection](xmpp-connection.md)
- [XMPP header enricher](xmpp-header-enricher.md)
  - [Chat thread id](xmpp-header-enricher---chat-thread-id.md)
  - [Chat to](xmpp-header-enricher---chat-to.md)
- [XMPP inbound channel adapter](xmpp-inbound-channel-adapter.md)
- [XMPP outbound channel adapter](xmpp-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [XMPP presence inbound channel adapter](xmpp-presence-inbound-channel-adapter.md)
- [XMPP presence outbound channel adapter](xmpp-presence-outbound-channel-adapter.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [XMPP presence to XML transformer](xmpp-presence-to-xml-transformer.md)

---

## <img src="img/InboundChannelAdaptor.png" height="30"/> Inbound channel adapters
- [JMX multi attribute polling message source](jmx-multi-attribute-polling-message-source.md)
- [Log appender channel adapter](log-appender-channel-adapter.md)

## <img src="img/InboundGateway.png" height="30"/> Inbound gateways
- [Command executor gateway](command-executor-gateway.md)

## <img src="img/OutboundChannelAdaptor.png" height="30"/> Outbound channel adapters
- [Logging channel adapter](logging-channel-adapter.md)
- ~~[Microflow invoking message consumer](microflow-invoking-message-consumer.md "Deprecated: use eMagiz Mendix Connector")~~
- ~~[XML mapping message consumer](xml-mapping-message-consumer.md "Deprecated: use eMagiz Mendix Connector")~~

## <img src="img/Transformer.png" height="30"/> Transformers
- [Base64 decoding transformer](base64-decoding-transformer.md)
- [Base64 encoding transformer](base64-encoding-transformer.md)
- [Character replacing transformer](character-replacing-transformer.md)
- EDI to XML transformer
- [Error to XML transformer](error-to-xml-transformer.md)
- Flat file to XML transformer
- [Header filter](header-filter.md)
- [Image transformer](image-transformer.md)
- [JSON to XML transformer](json-to-xml-transformer.md)
- [Mendix FileDocument WS request transformer](mendix-filedocument-ws-request-transformer.md)
- [Object to string transformer](object-to-string-transformer.md)
- UN/EDIFACT to XML transformer
- XML to EDI transformer
- XML to flat file transformer
- [XML to JSON transformer](xml-to-json-transformer.md)
- XML to UN/EDIFACT transformer

## <img src="img/Router.png" height="30"/> Routers
- [Header value router](header-value-router.md)
  - [Header value mapping](header-value-mapping.md)
- [Payload type router](payload-type-router.md)
  - [Payload type mapping](payload-type-mapping.md)
- [Recipient list router](recipient-list-router.md)
  - [Recipient](recipient.md)

## <img src="img/ServiceActivator.png" height="30"/> Service activators
- [Control bus](control-bus.md)
- [Custom error message activator](custom-error-message-activator.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- [Message bridge](message-bridge.md)
- [Mikrotik service activator](mikrotik-service-activator.md)
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- ThClient changes reading activator
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)
- ThClient table reading activator
  - [Expression evaluating request handler advice](expression-evaluating-request-handler-advice.md)
  - [Request handler circuit breaker advice](request-handler-circuit-breaker-advice.md)
  - [Request handler retry advice](request-handler-retry-advice.md)

## <img src="img/Channel.png" width="30"/> Channels
- [Default channel](channel.md)
  - [Debug interceptor](debug-interceptor.md)
  - ~~[Entry tracking interceptor](entry-tracking-interceptor.md "Deprecated: functionality replaced by debugging, flow testing, message archiving")~~
  - ~~[Exit tracking interceptor](exit-tracking-interceptor.md "Deprecated: functionality replaced by debugging, flow testing, message archiving")~~
  - [Wire tap](wire-tap.md)

## <img src="img/SupportObject.png" height="30"/> Support objects
- [Cache annotation driven](cache-annotation-driven.md)
- [Command controller](command-controller.md)
- [Composite cache manager](composite-cache-manager.md)
- [Concurrent map cache manager](concurrent-map-cache-manager.md)
- [Ehcache cache manager](ehcache-cache-manager.md)
  - [Ehcache cache](ehcache-cache.md)
- [Flow controller](flow-controller.md)
- [Global channel interceptor](global-channel-interceptor.md)
- [Global wire tap](global-wire-tap.md)
- [Management](management.md)
- [MBean export](mbean-export.md)
- [MBean server](mbean-server.md)
- [Message history](message-history.md)
- [OSGi service](osgi-service.md)
- [Performance monitor](jvm-performance-monitor.md)
- [Properties](properties.md)
- [Property placeholder](property-placeholder.md)
- [Simple cache manager](simple-cache-manager.md)
  - [Concurrent map cache](concurrent-map-cache.md)
- [Task executor](task-executor.md)
- ThClient connector
- [Top level poller](poller.md)
