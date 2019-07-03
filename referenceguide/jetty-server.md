---
id: jetty-server
title: Jetty Server
sidebar_label: Jetty Server
---
#### Jetty HTTP Servlet Server. 
<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Jetty_7_Architecture" target="_blank">Documentation</a>

This server aggregates <i>Connectors </i>(HTTP request receivers) and <i>request Handlers</i>. 


#### Connectors
Set the HTTP Connectors that use this server to handle HTTP requests. 

A connector receives requests (normally from a socket) and calls the handle method of this server to handle this requests.

Use a <i>Select Channel Connector</i> when there are many connections that have idle periods. 
Use a <i>Blocking channel selector</i> when there are a few very active connections.


#### Handler type
Responsible for handling incoming HTTP requests and sending the corresponding response.

<b>1. Coordinating Handlers</b>
<b>1.1 Handler List</b>
List of handlers which are called in turn until either an exception is thrown, the response is committed or a positive response status is set.
<b>1.2 Context Handler Collection</b>
Collection of <i>Context Handlers</i> of which some are selected by best match for the context path.
Multiple contexts may have the same context path and they are called in order until one handles the request.

<b>2. Filtering Handlers</b>
<b>2.1 Context Handler</b>
Group another handler below a particular <i>URI context path</i>
<b>2.2 Servlet Context Handler</b>
Extension to the <i>Context Handler</i> allows for simple construction of a context with a <i>Servlet Handler</i>
<b>2.3 Basic Security Handler</b>
Adds basic access authentication to the handler it wraps.

<b>3. Generating Handlers</b>
<b>3.1 Resource Handler</b>
Looks for a matching file in the local directory to serve.
<b>3.2 Servlet Handler</b>
Generates content by passing the request to a <i>Servlet</i> mapped by a URI pattern. Intended to be used when a full web application is not required. Specifically filters and request wrapping are not supported.

#### Graceful shutdown
Set graceful shutdown timeout. 

If set, shutting down the server will not immediately stop the server. Instead, all <i>Connectors</i> will be closed so that new connections will not be accepted and all <i>context</i>handlers will be put into the shutdown mode so that no new requests will be accepted, but existing requests can complete. 

The server will then wait the configured timeout before stopping.

#### Send date header
Wether to include the <code>Date</code> HTTP header in all responses.

Default is <code>false</code>.

#### Send server version
Wether to include the <code>Server</code> HTTP header in all responses.

Default is <code>false</code>.


<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Handlers" target="_blank">Documentation</a>

The resource handler is passed the request first and looks for a matching file in the local directory to serve. 
If a file is not found, then the request is passed to the default handler which generates a 404 (or favicon.ico). 

#### Resource base
Specifies where to look for the matching files.

#### Directories listed
If set, a listing of the content of a directory is returned when that directory inside the base directory matches the received request.

#### Aliases
Set if resource aliases (eg symlink, 8.3 names, case insensitivity) are allowed.

Allowing aliases can significantly increase security vulnerabilities. 


<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Servlets" target="_blank">Documentation</a>

Generates content by passing the request to a <i>Servlet</i> mapped by a URI pattern. Intended to be used when a full web application is not required. Specifically filters and request wrapping are not supported.



<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Context" target="_blank">Documentation</a>

Context handler that groups a Servlet handler below a particular URI context path 

#### Context path
Defines which requests are handled by this handler.

 eg: /myapp  


<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Handlers" target="_blank">Documentation</a>

List of handlers which are called in turn until either an exception is thrown, the response is committed or a positive response status is set.

<b>Context Handler </b> 
Group another handler below a particular <i>URI context path</i> 
<b>Servlet Context Handler</b> 
Extension to the <i>Context Handler</i> allows for simple construction of a context with a <i>Servlet Handler </i> 

<b>Resource Handler  </b>
Looks for a matching file in the local directory to serve. 
<b>Servlet Handler </b> 
Generates content by passing the request to a <i>Servlet</i> mapped by a URI pattern. Intended to be used when a full web application is not required. Specifically filters and request wrapping are not supported.


<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Handlers" target="_blank">Documentation</a>

Collection of <i>Context Handlers</i> of which some are selected by best match for the context path. 
Multiple contexts may have the same context path and they are called in order until one handles the request.

<b>Context Handler </b> 
Group another handler below a particular <i>URI context path</i> 
<b>Servlet Context Handler</b> 
Extension to the <i>Context Handler</i> allows for simple construction of a context with a <i>Servlet Handler </i> 

<b>Resource Handler  </b>
Looks for a matching file in the local directory to serve. 
<b>Servlet Handler </b> 
Generates content by passing the request to a <i>Servlet</i> mapped by a URI pattern. Intended to be used when a full web application is not required. Specifically filters and request wrapping are not supported.


<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Context" target="_blank">Documentation</a>

A ContextHandler is a HandlerWrapper that responds only to requests that have a URI prefix that matches the configured context path.


#### Context path
Defines which requests are handled by this handler.

 eg: /myapp  

#### Wrapped handler type
Specifies wrapped handler type.

<b>1. Resource Handler  </b>
Looks for a matching file in the local directory to serve. If a file is not found, then the request is passed to the default handler which generates a 404 (or favicon.ico). 
<b>2. Servlet Handler </b> 
Generates content by passing the request to a <i>Servlet</i> mapped by a URI pattern. 





<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Handlers" target="_blank">Documentation</a>

The resource handler is passed the request first and looks for a matching file in the local directory to serve. If a file is not found, then the request is passed to the default handler which generates a 404 (or favicon.ico). 

#### Resource base
Specifies where to look for the matching files.

#### Directories listed
If set, a listing of the content of a directory is returned when that directory inside the base directory matches the received request.

#### Aliases
Set if resource aliases (eg symlink, 8.3 names, case insensitivity) are allowed.

Allowing aliases can significantly increase security vulnerabilities. 


<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Servlets" target="_blank">Documentation</a>

The ServletHandler generates content by passing the request to a <i>Servlet</i> mapped by a <i>URI pattern</i>. 

First, the URI is matched against the mapping. The mapping maps URI's to servlet names. 
Second, the servlet(s) with the mapped names are resolved from the servlet list. This servlet(s) handles the received request.

<i>Note:
This handler is intended to be used when a full web application is not required. Specifically filters and request wrapping are not supported.</i>


A <b>very</b> basic security handler implementation that uses basic access authentication and checks against a static (in-memory) list of user credentials. Does not use any security constraints or user roles; any access to the handler it wraps simply requires one of the configured usernames and passwords.

#### Credentials
Comma-separated list of valid credentials for accessing the wrapped handler. Credentials must be written as a username & password pair with a colon (:) separating them. For example: <code>user1:PuYcRK92, user2:YpYp7gPe</code>

For flexibility, consider using a <code>${placeholder}</code> value.

<i>Required</i>

#### Wrapped handler type
Specifies wrapped handler type.

<b>Resource Handler</b>
Looks for a matching file in the local directory to serve. If a file is not found, then the request is passed to the default handler which generates a 404 (or favicon.ico). 

<b>Servlet Handler</b> 
Generates content by passing the request to a <i>Servlet</i> mapped by a URI pattern.


<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Handlers" target="_blank">Documentation</a>

The resource handler is passed the request first and looks for a matching file in the local directory to serve. If a file is not found, then the request is passed to the default handler which generates a 404 (or favicon.ico). 

#### Resource base
Specifies where to look for the matching files.

#### Directories listed
If set, a listing of the content of a directory is returned when that directory inside the base directory matches the received request.

#### Aliases
Set if resource aliases (eg symlink, 8.3 names, case insensitivity) are allowed.

Allowing aliases can significantly increase security vulnerabilities. 


<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Servlets" target="_blank">Documentation</a>

The ServletHandler generates content by passing the request to a <i>Servlet</i> mapped by a <i>URI pattern</i>. 

First, the URI is matched against the mapping. The mapping maps URI's to servlet names. 
Second, the servlet(s) with the mapped names are resolved from the servlet list. This servlet(s) handles the received request.

<i>Note:
This handler is intended to be used when a full web application is not required. Specifically filters and request wrapping are not supported.</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Servlets
Servlets receive and respond to requests from Web clients, usually across HTTP, the HyperText Transfer Protocol.

<b>Simple dispatcher servlet</b>
Delegates all request handling to the specified <i>Spring Web MVC Controller</i>. This controller uses the view resolver to create a reply message. 

<b>Web service message receiver servlet</b>
Delegates all request handling to the specified <i>Spring Web Services WebServiceMessageReceiver</i>.

#### Servlet mappings
Mapping from specific paths to servlet names. 

Servlets with these names should be specified.

#### Servlets
Servlets receive and respond to requests from Web clients, usually across HTTP, the HyperText Transfer Protocol.

<b>Simple dispatcher servlet</b>
Delegates all request handling to the specified <i>Spring Web MVC Controller</i>. This controller uses the view resolver to create a reply message. 

<b>Web service message receiver servlet</b>
Delegates all request handling to the specified <i>Spring Web Services WebServiceMessageReceiver</i>.

#### Servlet mappings
Mapping from specific paths to servlet names. 

Servlets with these names should be specified.

#### Servlets
Servlets receive and respond to requests from Web clients, usually across HTTP, the HyperText Transfer Protocol.

<b>Simple dispatcher servlet</b>
Delegates all request handling to the specified <i>Spring Web MVC Controller</i>. This controller uses the view resolver to create a reply message. 

<b>Web service message receiver servlet</b>
Delegates all request handling to the specified <i>Spring Web Services WebServiceMessageReceiver</i>.

#### Servlet mappings
Mapping from specific paths to servlet names. 

Servlets with these names should be specified.

#### Servlets
Servlets receive and respond to requests from Web clients, usually across HTTP, the HyperText Transfer Protocol.

<b>Simple dispatcher servlet</b>
Delegates all request handling to the specified <i>Spring Web MVC Controller</i>. This controller uses the view resolver to create a reply message. 

<b>Web service message receiver servlet</b>
Delegates all request handling to the specified <i>Spring Web Services WebServiceMessageReceiver</i>.

#### Servlet mappings
Mapping from specific paths to servlet names. 

Servlets with these names should be specified.

