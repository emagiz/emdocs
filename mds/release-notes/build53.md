Release notes for build number 53
Version 53, released 2020-09-04

Small update that makes XSD imports possible again, and improves the Kafka and OData support.

Major changes
- Kafka template and Kafka message listener container can now be configured with keystores and truststores uploaded as flow resources. Previously these could only be configured using files on disk.
- Flows that expose OData 4.01 endpoints using the 'simple OData servlet' option (located in the Jetty server support object) now also support querying for entities over associations (one-to-one, one-to-many, many-to-one and many-to-many).
- Before build number 50, it was possible to (manually) import one resource from another resource. In XSDs for example, you could add <xsd:import namespace="(...)" schemaLocation="another.xsd"/> to import another XSD. Because these imports work on any URI – such as "file:///etc/passwd" or "https://attacker.com/malicious.code" – this made XML External Entity (XXE) attacks possible. To remedy this, in build number 50 the Java settings accessExternalDTD, accessExternalSchema, and accessExternalStylesheet have been disabled. However, this made it impossible to use XSD imports. While eMagiz never generates XSDs containing imports, there are (valid) use-cases where you need this functionality. This release makes these imports work again, but only for trusted sources. "Trusted" here means resources that are uploaded to your flow only.

Minor changes
- Updated bundle 'com.emagiz.bundles.kafka-clients' from 2.4.0.1 to 2.4.0.2
- Updated bundle 'com.emagiz.bundles.spring-xml' from 3.0.8.1 to 3.0.8.2
- Updated bundle 'com.emagiz.components.kafka' from 2.0.0 to 2.0.1
- Updated bundle 'com.emagiz.components.odata' from 1.0.0 to 1.1.0
- Removed bundle 'com.emagiz.bundles.j8583' 1.5.1.1
- Removed bundle 'com.emagiz.components.iso8583' 6.0.0