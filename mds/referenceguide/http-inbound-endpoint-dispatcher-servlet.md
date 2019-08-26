---
id: http-inbound-endpoint-dispatcher-servlet
title: HTTP inbound endpoint dispatcher servlet
sidebar_label: HTTP inbound endpoint dispatcher servlet
---

A servlet that dispatches requests to <i>HTTP inbound gateways</i> and <i>HTTP inbound channel adapters</i> based on their <i>request mapping</i> settings:
- Path (required)
- Supported methods (required)
- Params (optional)
- Headers (optional)
- Consumes (optional)
- Produces (optional)

Any <i>HTTP inbound gateways</i> and <i>HTTP inbound channel adapters</i> that have a value for their <b>path</b> setting are auto-discovered by this servlet. Multiple HTTP inbound endpoints can share the same path, as long as they are configured for different HTTP methods (or any of the other optional settings mentioned above).
<hr/>Note that the full path in the URI is made up of multiple parts: <code>https://host:port/contextPath/servletPath/pathInfo?queryString</code>.

The <code>contextPath</code> is specified on Jetty's <i>servlet context handler</i>. The special value <code>/</code> can be used here to map all requests to the same servlet context handler.

The <code>servletPath</code> (also known as <i>path spec</i>) is configured on Jetty's <i>servlet mapping</i>. The special value <code>/*</code> can be used here to map all requests (within that servlet context handler's scope) to the same servlet.

The <code>pathInfo</code> is configured on your flow's <i>HTTP inbound gateways</i> and <i>HTTP inbound channel adapters</i> as the <b>path</b> setting. This setting cannot be empty and can contain path variables, for example <code>/order/{orderId}</code>. Together with the HTTP method (GET, PUT, POST, etc) and the other optional settings mentioned above this path is used to dispatch all incoming HTTP requests (within this servlet's scope) to the correct <i>HTTP inbound gateway</i> or <i>HTTP inbound channel adapter</i>.

If no <i>HTTP inbound gateway</i> or <i>HTTP inbound channel adapter</i> can be found that matches the path, method or any of the other optional settings of the request, this servlet will return an appropriate HTTP error. Some examples:
- <code>404 Not Found</code> : incorrect path (or correct path and method but incorrect header)
- <code>405 Request method 'PUT' not supported</code> : correct path but incorrect method
- <code>400 Parameter conditions "myParam=correct" not met for actual request parameters: myParam={wrong}</code> : correct path and method but incorrect param
- <code>415 Unsupported Media Type</code> : correct path and method but incorrect content type ("consumes")

