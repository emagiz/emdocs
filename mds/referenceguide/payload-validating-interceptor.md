---
id: payload-validating-interceptor
title: Payload validating interceptor
sidebar_label: Payload validating interceptor
---
#### Interceptor that validates the contents of Web Service messages using a schema. 
Allows for both W3C XML and RELAX NG schemas.

When the payload is invalid, this interceptor stops processing of the interceptor chain. Additionally, if the message is a SOAP request message, a SOAP Fault is created as reply. Invalid SOAP responses do not result in a fault.

By default, only the request message is validated, but this behaviour can be changed using the <i>validate Request</i> and <i>validate Response</i>  properties. Responses that contains faults are not validated.

#### XSD schema
Specifies the XSD schema to be used for validation.

#### Validate request
Indicates whether the request should be validated against the schema.

Default: true

#### Validate response
Indicates whether the response should be validated against the schema.

Default: false.

