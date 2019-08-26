---
id: simple-dispatcher-servlet
title: Simple dispatcher servlet
sidebar_label: Simple dispatcher servlet
---
#### An HTTP servlet that delegates all HTTP requests to a single handler.
<a href="http://static.springsource.org/spring/docs/3.1.x/spring-framework-reference/html/mvc.html#mvc-servlet" target="_blank">External documentation</a>

Creates a HTTP servlet that delegates all request handling to a single Spring Web MVC <code>Controller</code> or Spring Web <code>HttpRequestHandler</code>, for example a <i>HTTP inbound gateway</i> or a <i>HTTP inbound channel adapter</i>.

#### Name
The (unique) name for this servlet.

<i>Required</i>

#### Handler
The Spring Web MVC <code>Controller</code> or Spring Web <code>HttpRequestHandler</code> implementation that is used by this class for handling the HTTP request.

<i>Required</i>


Sets the resolvers to be used by the controller for resolving view names. 

The resolvers will be called in the list order until the name is resolved. If the name cannot be resolved by any of the resolvers, an exception is thrown when view name resolution is required.

Resolvers: 
1. <b>Bean name view resolver</b>
Interprets a view name as bean name in the current application context.

No resolvers are set by default. 


Sets the resolvers to use for resolving exceptions thrown during handler execution.

The resolvers will be called in the list order until the exception is resolved. If the exception cannot be resolved by any of the resolvers, it is just thrown by this servlet. 

Resolvers: 
1. <b>Default handler exception resolver</b>
Resolves standard Spring exceptions and translates them to corresponding HTTP status codes.

No resolvers are set by default.

---
id: simple-dispatcher-servlet
title: Simple dispatcher servlet
sidebar_label: Simple dispatcher servlet
---
#### An HTTP servlet that delegates all HTTP requests to a single handler.
<a href="http://static.springsource.org/spring/docs/3.1.x/spring-framework-reference/html/mvc.html#mvc-servlet" target="_blank">Documentation</a>

Creates a HTTP servlet that delegates all request handling to a single Spring Web MVC <code>Controller</code> or Spring Web <code>HttpRequestHandler</code>, for example a <i>HTTP inbound gateway</i> or a <i>HTTP inbound channel adapter</i>.

#### Name
The (unique) name for this servlet.

<i>Required</i>

#### Handler
The Spring Web MVC <code>Controller</code> or Spring Web <code>HttpRequestHandler</code> implementation that is used by this class for handling the HTTP request.

<i>Required</i>


Sets the resolvers to be used by the controller for resolving view names. 

The resolvers will be called in the list order until the name is resolved. If the name cannot be resolved by any of the resolvers, an exception is thrown when view name resolution is required.

Resolvers: 
1. <b>Bean name view resolver</b>
Interprets a view name as bean name in the current application context.

No resolvers are set by default. 


Sets the resolvers to use for resolving exceptions thrown during handler execution.

The resolvers will be called in the list order until the exception is resolved. If the exception cannot be resolved by any of the resolvers, it is just thrown by this servlet. 

Resolvers: 
1. <b>Default handler exception resolver</b>
Resolves standard Spring exceptions and translates them to corresponding HTTP status codes.

A single <i>default handler exception resolver</i> is also the default is nothing is specified.

