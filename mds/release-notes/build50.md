Release notes for build number 50
Version 50, released 2020-07-01

Large update moving most of the eMagiz runtime stack to the latest major versions of open source projects, libraries and technologies, most notably moving from Spring 4 to Spring 5. This update also brings new features to eMagiz, such as support for easy JSON transformations and validations using our integrated visual tooling.
New features
Flow components that operate on XML messages can now also be used on JSON messages. To make this possible new support objects 'JSON source factory', 'JSON result factory' and 'JSON result transformer' have been added. These support objects allow reading/writing JSON through the Java Streaming API for XML (StAX), adding JSON support to the following (existing) components:
XPath header enricher – This component can now evaluate XPath expressions on JSON messages to fill message headers.
XPath transformer – This component can now transform JSON messages using an XPath expression.
XPath router – This component can now do content based routing on JSON messages by evaluating an XPath expression.
XML validating filter – This component can now validate JSON messages against an XML schema (XSD).
XSLT transformer – This component can now perform transformations on JSON messages using XSLT stylesheets. The output can be JSON as well, allowing for JSON to JSON, JSON to XML, XML to JSON, and XML to XML transformations.
Major changes
Java 8 is now a hard requirement, Java 7 will no longer work. Since runtime version 4.1.6 (released 2017-06-30) it was possible to run on either Java 7 or Java 8: both were fully supported. Starting with runtime version 5.0.0 (released 2018-07-26), only Java 8 was supported. However at that point – by not using the latest runtime – flows could still be deployed on Java 7, but only if they did not use any of the newer features such as AMQP. From build number 50 onwards, deploying on Java 7 is no longer possible.
Completely dropped support for HornetQ in favour of AMQP (Apache ActiveMQ Artemis & Apache Qpid). HornetQ has not (yet) been removed from the flow designer, but from this build number onwards deploying flows containing HornetQ components is no longer possible. Older existing deployment packages with HornetQ will still work, but we urge you to update to AMQP as soon as possible if you haven't already.
We changed the way the internal message store (H2) behaves when shutting down: instead of waiting for all clients to disconnect, the server now terminates itself. This should make it much less likely that updating a running infra flow would "hang", requiring a full restart of the runtime. Instead, you'll now notice some connection errors from other flows trying to access the message store (H2) during the short window the infra flow is being replaced, but this is expected behaviour; after the new infra flow has started the connections should automatically re-establish themselves.
In previous Java versions, the "build-in" Java API for XML Processing (JAXP) implementations were quite outdated and contained some bugs that prevented some eMagiz components from functioning correctly. For this reason we overwrote these default "build-in" implementations with newer "stand-alone" versions. Starting with Java 8, the default "build-in" versions have be updated and are actually more stable than the "stand-alone" versions. That is why from this build number onwards we are switching back to the Java defaults and have removed the "stand-alone" versions, see also the removed bundles (such as Xerces) in the 'minor changes' section. For backwards compatibility, i.e. when mixing build 50 (and higher) and build 48 (and lower) flows in the same runtime, when we detect two conflicting versions of a JAXP implementation we now automatically force the Java default "build-in" version to be used. If for any reason an older flow depends on a specific implementation (which it shouldn't, but it is possible by writing "bad practice" Groovy scripts or SpEL expressions for example), the flow will stop working.
Minor changes
Added bundle 'com.emagiz.bundles.jxmpp-jid' 0.6.4.1
Added bundle 'com.emagiz.bundles.micrometer-core' 1.3.5.1
Added bundle 'com.emagiz.bundles.minidns-core' 0.3.4.1
Added bundle 'com.emagiz.bundles.reactor-core' 3.3.2.1
Added bundle 'com.emagiz.bundles.staxon' 1.3.0.1
Added bundle 'com.emagiz.components.staxon' 1.0.0
Added bundle 'com.emagiz.osgi.extender.staxon' 1.0.0
Added bundle 'com.emagiz.osgi.h2-destroy' 1.0.0
Added bundle 'com.emagiz.osgi.jaxp' 1.0.0
Added bundle 'org.apache.pdfbox.fontbox' 2.0.19
Added bundle 'org.jctools.core' 2.1.2
Added bundle 'org.reactivestreams.reactive-streams' 1.0.3
Updated bundle 'com.emagiz.batch.aws.redshift' from 1.2.0 to 2.0.0
Updated bundle 'com.emagiz.batch.azure.eventhubs' from 1.1.0 to 2.0.0
Updated bundle 'com.emagiz.batch.core' from 1.3.0 to 2.0.0
Updated bundle 'com.emagiz.batch.file' from 1.0.0 to 2.0.0
Updated bundle 'com.emagiz.batch.http' from 1.0.0 to 2.0.0
Updated bundle 'com.emagiz.batch.jdbc' from 1.1.0 to 2.0.0
Updated bundle 'com.emagiz.bundles.aws-java-sdk-all' from 1.11.460.1 to 1.11.720.1
Updated bundle 'com.emagiz.bundles.azure-eventhubs' from 1.0.2.1 to 3.0.2.1
Updated bundle 'com.emagiz.bundles.h2' from 1.4.197.2 to 1.4.199.1
Updated bundle 'com.emagiz.bundles.httpcomponents-client' from 4.5.6.1 to 4.5.11.1
Updated bundle 'com.emagiz.bundles.httpcomponents-core' from 4.4.10.1 to 4.4.13.1
Updated bundle 'com.emagiz.bundles.javax-servlet' from 2.6.0.1 to 3.1.0.1
Updated bundle 'com.emagiz.bundles.kafka-clients' from 0.11.0.3_1 to 2.4.0.1
Updated bundle 'com.emagiz.bundles.kafka-streams' from 0.11.0.3_1 to 2.4.0.1
Updated bundle 'com.emagiz.bundles.netty-buffer' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-codec' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-codec-http' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-codec-mqtt' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-common' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-handler' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-resolver' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-transport' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-transport-native-epoll' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-transport-native-kqueue' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.netty-transport-native-unix-common' from 4.1.34.1 to 4.1.50.1
Updated bundle 'com.emagiz.bundles.proton-j' from 0.31.0.1 to 0.33.5.1
Updated bundle 'com.emagiz.bundles.qpid-jms-client' from 0.40.0.1 to 0.48.0.1
Updated bundle 'com.emagiz.bundles.s3-stream-upload' from 1.0.1.1 to 2.1.0.1
Updated bundle 'com.emagiz.bundles.spring-aop' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-batch-core' from 3.0.9.1 to 4.2.1.1
Updated bundle 'com.emagiz.bundles.spring-batch-infrastructure' from 3.0.9.1 to 4.2.1.1
Updated bundle 'com.emagiz.bundles.spring-batch-integration' from 3.0.9.1 to 4.2.1.1
Updated bundle 'com.emagiz.bundles.spring-beans' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-context' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-context-support' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-core' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-expression' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-core' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-file' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-ftp' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-groovy' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-http' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-ip' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-jdbc' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-jms' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-jmx' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-kafka' from 2.3.0.1 to 3.2.1.1
Updated bundle 'com.emagiz.bundles.spring-integration-mail' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-scripting' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-sftp' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-ws' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-xml' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-integration-xmpp' from 4.3.17.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-jdbc' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-jms' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-kafka' from 1.3.9.1 to 2.4.1.1
Updated bundle 'com.emagiz.bundles.spring-messaging' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-oxm' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-retry' from 1.2.2.1 to 1.2.5.1
Updated bundle 'com.emagiz.bundles.spring-security-oauth2' from 2.1.3.1 to 3.0.0.ADAPT
Updated bundle 'com.emagiz.bundles.spring-security-config' from 4.2.8.1 to 5.0.0.ADAPT
Updated bundle 'com.emagiz.bundles.spring-security-core' from 4.2.8.1 to 5.0.0.ADAPT
Updated bundle 'com.emagiz.bundles.spring-security-web' from 4.2.8.1 to 5.0.0.ADAPT
Updated bundle 'com.emagiz.bundles.spring-tx' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-web' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-webmvc' from 4.3.20.1 to 5.2.3.1
Updated bundle 'com.emagiz.bundles.spring-ws-core' from 2.4.3.1 to 3.0.8.1
Updated bundle 'com.emagiz.bundles.spring-ws-security' from 2.4.3.1 to 3.0.8.1
Updated bundle 'com.emagiz.bundles.spring-ws-support' from 2.4.3.1 to 3.0.8.1
Updated bundle 'com.emagiz.bundles.spring-xml' from 2.4.3.1 to 3.0.8.1
Updated bundle 'com.emagiz.components' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.artemis' from 1.2.0 to 2.0.0
Updated bundle 'com.emagiz.components.batch' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.control' from 7.2.0 to 8.0.0
Updated bundle 'com.emagiz.components.debug' from 2.1.0 to 3.0.0
Updated bundle 'com.emagiz.components.ehcache' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.error' from 6.2.0 to 7.0.0
Updated bundle 'com.emagiz.components.file' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.ftp' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.http' from 6.0.0 to 7.0.0
Updated bundle 'com.emagiz.components.iso8583' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.jdbc' from 5.4.0 to 6.0.0
Updated bundle 'com.emagiz.components.jms' from 5.1.0 to 6.0.0
Updated bundle 'com.emagiz.components.jmx' from 6.0.0 to 7.0.0
Updated bundle 'com.emagiz.components.json' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.kafka' from 1.0.0 to 2.0.0
Updated bundle 'com.emagiz.components.logging' from 6.3.0 to 7.0.0
Updated bundle 'com.emagiz.components.mail' from 5.0.3 to 6.0.0
Updated bundle 'com.emagiz.components.mapping' from 6.0.0 to 7.0.0
Updated bundle 'com.emagiz.components.monitoring' from 6.0.0 to 7.0.0
Updated bundle 'com.emagiz.components.qpid' from 1.0.2 to 2.0.0
Updated bundle 'com.emagiz.components.security' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.sftp' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.smooks' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.tcp' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.thclient' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.tracking' from 6.0.0 to 7.0.0
Updated bundle 'com.emagiz.components.ws' from 5.1.0 to 6.0.0
Updated bundle 'com.emagiz.components.wssec' from 1.0.0 to 2.0.0
Updated bundle 'com.emagiz.components.xml' from 5.0.1 to 6.0.0
Updated bundle 'com.emagiz.components.xmpp' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.components.xslfo' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.osgi.extender.batch' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.osgi.extender.commandexecution' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.osgi.extender.core' from 5.2.0 to 6.0.0
Updated bundle 'com.emagiz.osgi.extender.infraresources' from 1.0.0 to 2.0.0
Updated bundle 'com.emagiz.osgi.extender.jms' from 1.3.1 to 2.0.0
Updated bundle 'com.emagiz.osgi.extender.mapping' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.osgi.extender.unittest' from 1.0.0 to 2.0.0
Updated bundle 'com.emagiz.osgi.extender.xml' from 5.0.4 to 6.0.0
Updated bundle 'com.emagiz.osgi.services' from 1.0.0 to 2.0.0
Updated bundle 'com.emagiz.util' from 4.3.0 to 5.0.0
Updated bundle 'com.emagiz.util.codec' from 5.0.0 to 6.0.0
Updated bundle 'com.emagiz.util.xml' from 4.0.2 to 5.0.0
Updated bundle 'com.fasterxml.jackson.core.jackson-annotations' from 2.7.9 to 2.10.2
Updated bundle 'com.sun.jna' from 4.1.0 to 5.5.0
Updated bundle 'io.dropwizard.metrics.core' from 3.2.6 to 4.1.5
Updated bundle 'joda-time' from 2.10.1 to 2.10.5
Updated bundle 'org.apache.commons.commons-beanutils' from 1.9.3 to 1.9.4
Updated bundle 'org.apache.commons.commons-codec' from 1.11.0 to 1.13.0
Updated bundle 'org.apache.commons.net' from 3.4.0 to 3.6.0
Updated bundle 'org.apache.santuario.xmlsec' from 2.1.1 to 2.1.4
Updated bundle 'org.apache.servicemix.bundles.jsch' from 0.1.54.1 to 0.1.55.1
Updated bundle 'org.apache.servicemix.bundles.xalan' from 2.7.1.8 to 2.7.2.3
Updated bundle 'org.apache.servicemix.bundles.xmlgraphics-commons' from 1.5.0.1 to 2.4.0.1
Updated bundle 'org.apache.wss4j.wss4j-ws-security-common' from 2.2.1 to 2.2.2
Updated bundle 'org.apache.wss4j.wss4j-ws-security-dom' from 2.2.1 to 2.2.2
Updated bundle 'org.eclipse.gemini.blueprint.core' from 2.1.0.RELEASE to 3.0.0.M01
Updated bundle 'org.eclipse.gemini.blueprint.extender' from 2.1.0.RELEASE to 3.0.0.M01
Updated bundle 'org.eclipse.gemini.blueprint.io' from 2.1.0.RELEASE to 3.0.0.M01
Updated bundle 'org.igniterealtime.smack.resolver-javax' from 4.1.7 to 4.3.4
Updated bundle 'org.igniterealtime.smack.sasl-javax' from 4.1.7 to 4.3.4
Updated bundle 'org.jxmpp.util-cache' from 0.4.2 to 0.6.4
Replaced bundle 'com.emagiz.bundles.ehcache-core' 2.6.9.1 with 'com.emagiz.bundles.ehcache' 2.10.6.1
Replaced bundle 'com.fasterxml.jackson.core.jackson-core' 2.7.9 with 'com.emagiz.bundles.fasterxml-jackson-core' 2.10.2.1
Replaced bundle 'com.fasterxml.jackson.core.jackson-databind' 2.7.9.4 with 'com.emagiz.bundles.jackson-databind' 2.10.2.1
Replaced bundle 'groovy-all' 2.4.15 with 'com.emagiz.bundles.groovy-all' 2.5.8.1
Replaced bundle 'org.apache.servicemix.bundles.batik' 1.7.0.3 with 'com.emagiz.bundles.batik' 1.12.1
Replaced bundle 'org.apache.servicemix.bundles.fop' 1.1.0.1 with 'com.emagiz.bundles.fop' 2.4.0.1
Replaced bundle 'org.apache.servicemix.bundles.jasypt' 1.9.2.1 with 'com.emagiz.bundles.jasypt' 1.9.3.1
Replaced bundle 'org.apache.servicemix.bundles.opensaml' 3.3.0.2 with 'com.emagiz.bundles.opensaml' 3.4.3.1
Replaced bundle 'org.apache.servicemix.bundles.saxon' 9.4.0.7_1 with 'com.emagiz.bundles.saxon' 10.1.0.1
Replaced bundle 'org.apache.servicemix.bundles.xmlpull' 1.1.3.4a_1 with 'org.apache.servicemix.bundles.xpp3' 1.1.4.c
Replaced bundle 'org.eclipse.jetty.continuation' 8.1.15.v20140411 with 'com.emagiz.bundles.jetty-continuation' 9.4.26.1
Replaced bundle 'org.eclipse.jetty.http' 8.1.15.v20140411 with 'com.emagiz.bundles.jetty-http' 9.4.26.1
Replaced bundle 'org.eclipse.jetty.io' 8.1.15.v20140411 with 'com.emagiz.bundles.jetty-io' 9.4.26.1
Replaced bundle 'org.eclipse.jetty.security' 8.1.15.v20140411 with 'com.emagiz.bundles.jetty-security' 9.4.26.1
Replaced bundle 'org.eclipse.jetty.server' 8.1.15.v20140411 with 'com.emagiz.bundles.jetty-server' 9.4.26.1
Replaced bundle 'org.eclipse.jetty.servlet' 8.1.15.v20140411 with 'com.emagiz.bundles.jetty-servlet' 9.4.26.1
Replaced bundle 'org.eclipse.jetty.util' 8.1.15.v20140411 with 'com.emagiz.bundles.jetty-util' 9.4.26.1
Replaced bundle 'org.igniterealtime.smack.core' 4.1.7 with 'com.emagiz.bundles.smack-core' 4.3.4.1
Replaced bundle 'org.igniterealtime.smack.extensions' 4.1.7 with 'com.emagiz.bundles.smack-extensions' 4.3.4.1
Replaced bundle 'org.igniterealtime.smack.im' 4.1.7 with 'com.emagiz.bundles.smack-im' 4.3.4.1
Replaced bundle 'org.igniterealtime.smack.java7' 4.1.7 with 'com.emagiz.bundles.smack-java7' 4.3.4.1
Replaced bundle 'org.igniterealtime.smack.tcp' 4.1.7 with 'com.emagiz.bundles.smack-tcp' 4.3.4.1
Replaced bundle 'org.jxmpp.core' 0.4.2 with 'com.emagiz.bundles.jxmpp-core' 0.6.4.1
Removed bundle 'com.emagiz.bundles.hornetq' 2.3.25.3
Removed bundle 'com.emagiz.components.eaas' 4.0.0
Removed bundle 'com.emagiz.components.hornetq' 5.0.0
Removed bundle 'com.emagiz.osgi.eaas' 5.1.0
Removed bundle 'com.emagiz.osgi.extender.eaas' 5.0.0
Removed bundle 'com.emagiz.osgi.extender.spring2.compatibility' 1.0.3
Removed bundle 'com.springsource.javax.jms' 1.1.0
Removed bundle 'org.apache.servicemix.bundles.xerces' 2.11.0.1
Removed bundle 'org.apache.servicemix.bundles.xmlresolver' 1.2.0.5
Removed bundle 'org.jboss.logging.jboss-logging' 3.1.4.GA
Removed bundle 'org.jboss.netty' 3.6.10.Final
Removed bundle 'org.jgroups' 3.6.15.Final
Known issues
Flows containing a Jetty server (support object), primarily used to host REST and SOAP web services, require some special attention when deploying because not all combinations of build number 50 (and higher) and 48 (and lower) flows will work correctly:
After installing any build 50 (or higher) flow, build 48 (or lower) flows containing a Jetty server on the same runtime cannot be started anymore. If it is really necessary to still install/start a build 48 (or lower) Jetty server flow: uninstall all build 50 (or higher) flows on that runtime first, then install/start the build 48 (or lower) Jetty server flow, and finally re-install the build 50 (or higher) flows.
When deploying a flow containing a Jetty server, the infra flow of that runtime must have a matching build number, that is: if the the Jetty server flow is build 48 (or lower) the infra needs to be build 48 (or lower) as well, if the Jetty server flow is build 50 (or higher) the infra needs to be 50 (or higher) as well.
Previously, it was possible to (manually) import one resource from another resource. In XSDs for example, you could add <xsd:import namespace="(...)" schemaLocation="another.xsd"/> to import another XSD. Because these imports work on any URI – such as "file:///etc/passwd" or "https://attacker.com/malicious.code" – this makes XML External Entity (XXE) attacks possible. To remedy this, the Java settings accessExternalDTD, accessExternalSchema, and accessExternalStylesheet have been disabled. However, this makes it impossible to use XSD imports. XSD includes can be replaced by simply merging the files, but for XSD imports there is no alternative. While eMagiz never generates XSDs containing imports, we are aware that there are (valid) use-cases where you need this functionality. We are looking into making imports work again in a future release, but for trusted sources only.
Remarks
The "Spring 2 compatibility mode", introduced in the release of 2017-11-16 to make the migration from Spring 2 (build 22 and earlier) to Spring 4 (build 23 to 49) based eMagiz flows easier, can no longer be used. Spring 4 (build 23 to 49) and Spring 5 (build 50 and newer) based eMagiz flow are fully compatible and require no special "compatibility mode".
This release updates the Groovy scripting language from version 2.4.15 to version 2.5.8. While mostly compatible, this could cause problems with existing (older) Groovy scripts, so we recommend testing your flows that contain any (custom) Groovy scripts in this new build number. Additionally, this release contains a lot of Java library changes (see the 'minor changes' section): if your Groovy scripts were programmed against any of these libraries you might have to update those scripts.
Both the 'mail inbound channel adapter' and the 'IMAP idle channel adapter' now automatically close the connection to the remote mail folder after fetching mail. This can cause problems in certains flows, particularly when mail attachments are accessed/downloaded further downstream. This behaviour can be changed by disabling the new 'auto-close folder' option on the mail inbound / IMAP idle channel adapter. If you do, you have to make sure the downstream flow at some points correctly closes the connection. This can be done by using the SpEL expression "headers.closeableResource.close()" whenever it is necessary, for example as part of a 'request handler advice chain' or by using an explicit flow component such as a 'standard service activator'.
We went from build number 48 to 50, skipping number 49. This way the number "50" is a nice indicator for the underlying technology change from Spring 4 to Spring 5.