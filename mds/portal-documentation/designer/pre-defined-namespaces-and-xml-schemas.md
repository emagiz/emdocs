# Pre-defined namespaces and XML schemas

https://my.emagiz.com/link/documentation/6

Some of the messaging components of eMagiz use XML messages in a pre-defined format. Each of these XML formats has its own namespace and XML schema definition, which are listed in the table below.  

| **Namespace** | **Description** | **XML schema** |
| :--- | :--- | :--- |
| http://www.emagiz.com/ns/beans/1.0/	|  eMagiz extension of Spring bean definition XML format	|  classpath:com/emagiz/core/beans/emagiz-beans-1.0..xsd |
| http://www.emagiz.com/ns/error/2.0/	| Output format of error to XML transformer.  Input format of eMagiz message tracking module (Mendix) | classpath:com/emagiz/components/error/emagiz-error-2.0.xsd |
| http://www.emagiz.com/ns/http/1.0/	| Output format of HTTP parameter map to XML transformer |	 classpath:com/emagiz/components/http/emagiz-http-1.0.xsd |
| http://www.emagiz.com/ns/iso8583/1.0/	| Output format of ISO8583 bytes to XML transformer.  Input format of ISO8583 XML to bytes transformer	| classpath:com/emagiz/components/iso8583/emagiz-iso8583-1.0.xsd |
| http://www.emagiz.com/ns/jdbc/1.0/	| Output format of JDBC result set to XML transformer	| classpath:com/emagiz/components/jdbc/emagiz-jdbc-1.0.xsd |
| http://www.emagiz.com/ns/jmx/2.0/	| Output format of JMX multi attribute polling message source.  Input format of eMagiz monitoring process	| classpath:com/emagiz/components/jmx/emagiz-jmx-2.0.xsd  |
| http://www.emagiz.com/ns/json/1.0/	| Output format of JSON to XML transformer.  Input format of XML to JSON transformer	| classpath:com/emagiz/components/json/emagiz-json-1.0.xsd |
| http://www.emagiz.com/ns/logging/2.0/ | Output format of Log appender channel adapter.  Input format of eMagiz monitoring module (Mendix) | classpath:com/emagiz/components/json/emagiz-logging-2.0.xsd |
| http://www.emagiz.com/ns/mail/1.0/	| Input format of Mail XML to MIME message transformer	| classpath:com/emagiz/components/mail/emagiz-mail-1.0.xsd |
| http://www.emagiz.com/ns/mapping/1.0/	| Message format of eMagiz mapping service	| classpath:com/emagiz/components/mapping/emagiz-mapping-1.0.xsd |
| http://www.emagiz.com/ns/monitoring/1.0/	| Output format of eMagiz monitoring process.  Input format of eMagiz monitoring module (Mendix)	| classpath:com/emagiz/components/monitoring/emagiz-monitoring-1.0.xsd |
| http://www.emagiz.com/ns/tracking/2.0/	| Output format of message tracking channel interceptors.  Input format of eMagiz message tracking module (Mendix)	| classpath:com/emagiz/components/tracking/emagiz-tracking-2.0.xsd |
| http://www.emagiz.com/ns/xmpp/1.0/	| Output format of XMPP presence to XML transformer	| classpath:com/emagiz/components/xmpp/emagiz-xmpp-1.0.xsd |  

You can download all of these XML schemas from the store at https://my.emagiz.com/link/app/558  
Or the most-used specific ones:  mail, JSON, and error messages. 
 
_Note:_ the values in the table above for _XML schema_ are valid resource references that can be used in eMagiz flows. For example, you can use this value to specify the _XSD resource_ of an _XML validating filter_.
