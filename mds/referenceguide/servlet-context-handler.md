---
id: servlet-context-handler
title: Servlet context handler
sidebar_label: Servlet context handler
---
#### Context handler that groups a Servlet handler below a particular URI context path 
<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Context" target="_blank">External documentation</a>

Extension to the <i>Context Handler</i> allows for simple construction of a context with a <i>Servlet Handler </i> 

It responds only to requests that have a URI prefix that matches the configured context path.


#### Context path
Defines which requests are handled by this handler.

examples:
<code>/ws</code> - handles all request to path '/ws'
<code>/</code>  - handles all requests

#### Servlets
Servlets receive and respond to requests from Web clients, usually across HTTP, the HyperText Transfer Protocol.

<b>Simple dispatcher servlet</b>
Delegates all request handling to the specified <i>Spring Web MVC Controller</i>. This controller uses the view resolver to create a reply message. 

<b>Web service message receiver servlet</b>
Delegates all request handling to the specified <i>Spring Web Services WebServiceMessageReceiver</i>.

#### Servlet mappings
Mapping from specific paths to servlet names. Servlets with these names should be specified.


---
id: servlet-context-handler
title: Servlet context handler
sidebar_label: Servlet context handler
---
#### Context handler that groups a Servlet handler below a particular URI context path 
<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Context" target="_blank">Documentation</a>

Extension to the <i>Context Handler</i> allows for simple construction of a context with a <i>Servlet Handler </i> 

It responds only to requests that have a URI prefix that matches the configured context path.


#### Context path
Defines which requests are handled by this handler, for example <code>/ws</code> or <code>/rest</code>.

The special value <code>/</code> (the root context) can be used here to map all requests to the same servlet context handler.

Note that the full path in the URI is made up of multiple parts: <code>https://host:port/contextPath/servletPath/pathInfo?queryString</code>.

#### Servlets
Servlets receive and respond to requests from Web clients, usually across HTTP, the HyperText Transfer Protocol.

<b>Web service message receiver servlet</b>
Delegates all request handling to the specified <i>Spring Web Services WebServiceMessageReceiver</i>.

<b>HTTP inbound endpoint dispatcher servlet</b>
Dispatches requests to <i>HTTP inbound gateways</i> and <i>HTTP inbound channel adapters</i> based on the path and HTTP method.

<b>Simple dispatcher servlet</b>
Delegates all request handling to the specified <i>Spring Web MVC Controller</i>. This controller uses the view resolver to create a reply message. 

#### Servlet mappings
Mapping from specific paths to servlet names. Servlets with these names should be specified.


