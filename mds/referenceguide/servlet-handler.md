---
id: servlet-handler
title: Servlet handler
sidebar_label: Servlet handler
---
#### Handler that generates content by passing the request to a Servlet mapped by a URI pattern. 
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

