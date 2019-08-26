---
id: servlet-mapping
title: Servlet mapping
sidebar_label: Servlet mapping
---
#### Path spec
URI to be mapped to the servlet.

example
<code>/*</code> - matches all paths in this context
<code>/ws1</code> 

#### Servlet name
Name of the servlet.

A servlet with this name have to be specified.

---
id: servlet-mapping
title: Servlet mapping
sidebar_label: Servlet mapping
---
#### Path spec
The <code>servletPath</code> (also known as <i>path spec</i>) to be mapped to the specified servlet, for example <code>/crm-connector/*</code>.

The special value <code>/*</code> can be used here to map all requests (within this servlet context handler's scope) to the same servlet.

Note that the full path in the URI is made up of multiple parts: <code>https://host:port/contextPath/servletPath/pathInfo?queryString</code>.

#### Servlet name
Name of the servlet, for example <code>crm-servlet</code>.

A servlet with this exact name must exist.

