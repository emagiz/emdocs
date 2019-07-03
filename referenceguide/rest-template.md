---
id: rest-template
title: REST template
sidebar_label: REST template
---

Intercepts client-side HTTP requests, providing the opportunity to modify the outgoing HTTP request and/or the incoming HTTP reponse.

This can be used to add authentication to HTTP connections, for example.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Type
By default a <code>RestTemplate</code> relies on standard JDK facilities to establish HTTP connections. This option allows you to switch to a different HTTP library.

<b>Note that the standard JDK HTTP library does not support the HTTP PATCH method.</b> Configure the <i>Apache HttpComponents</i> request factory to enable PATCH.

#### Buffer request body
Whether this request factory should buffer the request body internally.

Default is <code>true</code>. When sending large amounts of data via POST or PUT, it is recommended to change this property to <code>false</code>, so as not to run out of memory.

#### Connect timeout
The connection timeout (in milliseconds) for the underlying <code>HttpClient</code>. A timeout value of <code>0</code> specifies an infinite timeout.

Default is the value specified in the Java system properties.

#### Read timeout
The socket read timeout (in milliseconds) for the underlying <code>HttpClient</code>. A timeout value of <code>0</code> specifies an infinite timeout.

Default is the value specified in the Java system properties.

