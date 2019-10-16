Small update that improves REST support and error handling.
## New features
- When a HTTP/REST call fails and the server returns a response body (usually providing more details about the error), this information is now automatically added to the error messages created by the 'error to XML transformer'.
- The 'error to XML transformer' has the following new features, all in support of the improved eMagiz best practices for error handling in synchronous bus flows:
  - Added a new option to log every exception (payload of the input messages) as a warning. This can be useful if the error handling further downstream can not always be relied on, for example when sending errors back upstream in synchronous flows. In such cases having at least logged the initial exception might help doing root cause analyses.
  - Every error message created by this transformer now has the 'emagiz_error_isErrorMessage=true' message header. This header can be used further downstream in the flow to very quickly and efficiently distinguish between "normal" messages and error messages.
  - If an incoming exception contains the new special marker exception 'AsyncHandledException' anywhere in the exception hierarchy, the error will not be transformed to XML but instead the exception is rethrown. This is to guard against re-entry of a flow's error handling in case we want to intentionally signal a failure to the originating thread after (successfully) handling the error asynchronously.
- New 'HTTP inbound endpoint dispatcher servlet' added as a replacement for the 'simple dispatcher servlet'. Using this new dispatcher servlet "unlocks" the following new features in HTTP inbound gateways and HTTP inbound channel adapters:
  - Automatic discovery of all 'HTTP inbound gateways' and 'HTTP inbound channel adapters'.
  - Smart mapping of requests to the endpoint that best matches the request path, method, params, headers and content type.
  - Fully configurable path that can include {variables} and wildcards (?, *, **). Requests will automatically be mapped to the most precise matching path (more wildcards makes a path less precise). Specifying multiple endpoints using the exact same path is also supported, as long as there is some other differentiating factor such as the HTTP method.
  -All information of the incoming request (path variables, parameters, headers, etc.) is available for specifying header values and the payload content of the resulting message.
## Major changes
- The 'simple dispatcher servlet' now supports HTTP method PATCH, and has the 'default handler exception resolver' as the default handler exception resolver (previously it had none). These changes should not really affect existing published HTTP/REST endpoints, however the 'simple dispatcher servlet' has now also been deprecated in favour of the new 'HTTP inbound endpoint dispatcher servlet'. Since this new dispatcher servlet has way more features than the old one and is configured quite differently, we decided not to change any existing flows to avoid breaking those. But we strongly encourage you to take a look at the new features and start replacing your old 'simple dispatcher servlets'.
## Minor changes
- Updated bundle 'com.emagiz.components.error' from 6.1.0 to 6.2.0
- Updated bundle 'com.emagiz.components.http' from 5.0.1 to 6.0.0
