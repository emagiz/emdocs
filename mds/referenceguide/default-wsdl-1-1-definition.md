---
id: default-wsdl-1-1-definition
title: Default WSDL 1.1 definition
sidebar_label: Default WSDL 1.1 definition
---
#### Dynamic WSDL definition that creates a SOAP binding based on XSD schemas.
<a href="http://docs.spring.io/spring-ws/sites/2.0/reference/html/server.html#server-automatic-wsdl-exposure" target="_blank">External documentation</a>

The <i>Default Wsdl11 Definition </i>builds a WSDL from a XSD schema.  
This definition iterates over all element elements found in the schema, and creates a message for all elements. Next, it creates <i>WSDL operation </i> for all messages that end with the defined request or response suffix. (The default request suffix is <i>Request</i>; the default response suffix is <i>Response</i>)
It also builds a <i>portType, binding,</i> and <i>service</i> based on the operations.

Example:
<code>id="orders" 
portTypeName="Orders" 
locationUri ="http://localhost:8080/ordersService/" 

schema xsd="/WEB-INF/xsd/Orders.xsd" </code>

For instance, if <i>Orders.xsd</i> schema defines the <i>GetOrdersRequest</i> and <i>GetOrdersResponse</i> elements, the  a <i>GetOrdersRequest </i>and <i>GetOrdersResponse</i> message will be created, and a <i>GetOrders</i> operation, which is put in a <i>Orders</i> port type. 

#### XSD schema
An XSD schema to base the WSDL on.

#### Port type name
The port type name used for this definition. 

#### Create SOAP 1.1 binding
Indicates whether a SOAP 1.1 binding should be created.

Defaults to true.

#### Create SOAP 1.2 binding
Indicates whether a SOAP 1.2 binding should be created.

#### Location URI
The value used for the SOAP Address location attribute value.

Required.

#### Service name
The service name.

Defaults to the port type name, with the suffix 'Service' appended to it.

#### Target namespace
The target namespace used for this definition.

Defaults to the target namespace of the defined schema.

#### Request suffix
The suffix used to detect request elements in the schema.

Defaults to 'Request'.
                    

#### Response suffix
The suffix used to detect response elements in the schema.

Defaults to 'Response'.

#### Fault suffix
The suffix used to detect fault elements in the schema.

Defaults to 'Fault'.

#### Transport URI
The value used for the binding transport attribute value. 

Defaults to HTTP.


By default all the web service operations are created without a value for the <i>SOAP action</i> HTTP header, i.e. <code>soapAction=""</code>.

To include a value for the <i>SOAP action</i> of a specific operation in the generated WSDL, specify it here.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: default-wsdl-1-1-definition
title: Default WSDL 1.1 definition
sidebar_label: Default WSDL 1.1 definition
---
#### Dynamic WSDL definition that creates a SOAP binding based on XSD schemas.
<a href="http://docs.spring.io/spring-ws/sites/2.0/reference/html/server.html#server-automatic-wsdl-exposure" target="_blank">Documentation</a>

The <i>Default Wsdl11 Definition </i>builds a WSDL from a XSD schema.  
This definition iterates over all element elements found in the schema, and creates a message for all elements. Next, it creates <i>WSDL operation </i> for all messages that end with the defined request or response suffix. (The default request suffix is <i>Request</i>; the default response suffix is <i>Response</i>)
It also builds a <i>portType, binding,</i> and <i>service</i> based on the operations.

Example:
<code>id="orders" 
portTypeName="Orders" 
locationUri ="http://localhost:8080/ordersService/" 

schema xsd="/WEB-INF/xsd/Orders.xsd" </code>

For instance, if <i>Orders.xsd</i> schema defines the <i>GetOrdersRequest</i> and <i>GetOrdersResponse</i> elements, the  a <i>GetOrdersRequest </i>and <i>GetOrdersResponse</i> message will be created, and a <i>GetOrders</i> operation, which is put in a <i>Orders</i> port type. 

#### XSD schema
An XSD schema to base the WSDL on.

#### Port type name
The port type name used for this definition. 

#### Create SOAP 1.1 binding
Indicates whether a SOAP 1.1 binding should be created.

Defaults to true.

#### Create SOAP 1.2 binding
Indicates whether a SOAP 1.2 binding should be created.

#### Location URI
The value used for the SOAP Address location attribute value.

Required.

#### Service name
The service name.

Defaults to the port type name, with the suffix 'Service' appended to it.

#### Target namespace
The target namespace used for this definition.

Defaults to the target namespace of the defined schema.

#### Request suffix
The suffix used to detect request elements in the schema.

Defaults to 'Request'.
                    

#### Response suffix
The suffix used to detect response elements in the schema.

Defaults to 'Response'.

#### Fault suffix
The suffix used to detect fault elements in the schema.

Defaults to 'Fault'.

#### Transport URI
The value used for the binding transport attribute value. 

Defaults to HTTP.


By default all the web service operations are created without a value for the <i>SOAP action</i> HTTP header, i.e. <code>soapAction=""</code>.

To include a value for the <i>SOAP action</i> of a specific operation in the generated WSDL, specify it here.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

