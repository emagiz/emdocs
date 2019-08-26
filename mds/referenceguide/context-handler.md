---
id: context-handler
title: Context handler
sidebar_label: Context handler
---
#### Context handler that groups another handler below a particular URI context path 
<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Context" target="_blank">External documentation</a>

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





<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Handlers" target="_blank">External documentation</a>

The resource handler is passed the request first and looks for a matching file in the local directory to serve. If a file is not found, then the request is passed to the default handler which generates a 404 (or favicon.ico). 

#### Resource base
Specifies where to look for the matching files.

#### Directories listed
If set, a listing of the content of a directory is returned when that directory inside the base directory matches the received request.

#### Aliases
Set if resource aliases (eg symlink, 8.3 names, case insensitivity) are allowed.

Allowing aliases can significantly increase security vulnerabilities. 


<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Servlets" target="_blank">External documentation</a>

The ServletHandler generates content by passing the request to a <i>Servlet</i> mapped by a <i>URI pattern</i>. 

First, the URI is matched against the mapping. The mapping maps URI's to servlet names. 
Second, the servlet(s) with the mapped names are resolved from the servlet list. This servlet(s) handles the received request.

<i>Note:
This handler is intended to be used when a full web application is not required. Specifically filters and request wrapping are not supported.</i>

#### Servlets
Servlets receive and respond to requests from Web clients, usually across HTTP, the HyperText Transfer Protocol.

<b>Simple dispatcher servlet</b>
Delegates all request handling to the specified <i>Spring Web MVC Controller</i>. This controller uses the view resolver to create a reply message. 

<b>Web service message receiver servlet</b>
Delegates all request handling to the specified <i>Spring Web Services WebServiceMessageReceiver</i>.

#### Servlet mappings
Mapping from specific paths to servlet names. 

Servlets with these names should be specified.

---
id: context-handler
title: Context handler
sidebar_label: Context handler
---
#### Context handler that groups another handler below a particular URI context path 
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

#### Servlets
Servlets receive and respond to requests from Web clients, usually across HTTP, the HyperText Transfer Protocol.

<b>Simple dispatcher servlet</b>
Delegates all request handling to the specified <i>Spring Web MVC Controller</i>. This controller uses the view resolver to create a reply message. 

<b>Web service message receiver servlet</b>
Delegates all request handling to the specified <i>Spring Web Services WebServiceMessageReceiver</i>.

#### Servlet mappings
Mapping from specific paths to servlet names. 

Servlets with these names should be specified.

