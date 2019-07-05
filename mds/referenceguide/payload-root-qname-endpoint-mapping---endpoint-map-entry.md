---
id: payload-root-qname-endpoint-mapping---endpoint-map-entry
title: Payload root QName endpoint mapping - endpoint map entry
sidebar_label: Payload root QName endpoint mapping - endpoint map entry
---
#### Defines a mapping between a message request and endpoints
Specifies the mapping between qualified payload root name and endpoints.

A qualified name consists of a namespace URI and a local part, the combination of which should be unique within the mapping. 

The qualified name is expressed as { + namespace URI + } + local part. 

examples:
<code>
{http://samples}orderRequest 	-> getOrderEndPoint
{http://samples}order 		-> createOrderEndPoint
</code>


