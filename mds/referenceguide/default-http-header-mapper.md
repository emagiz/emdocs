---
id: default-http-header-mapper
title: Default HTTP header mapper
sidebar_label: Default HTTP header mapper
---
#### Inbound header names
Provide the header names that should be mapped from an HTTP request (for inbound adapters) or HTTP response (for outbound adapters) to message headers. The values can also contain simple wildcard patterns (e.g. <code>foo*</code> or <code>*foo</code>) to be matched.

This will match the header name directly or, for non-standard HTTP headers, it will match the header name prefixed with the value specified by the <i>user defined header prefix</i> setting (default: empty string).

The strings <code>HTTP_REQUEST_HEADERS</code> and <code>HTTP_RESPONSE_HEADERS</code> will match against any of the standard HTTP request and response headers, respectively.

#### Outbound header names
Provide the header names that should be mapped to an HTTP request (for outbound adapters) or HTTP response (for inbound adapters) from message headers. The values can also contain simple wildcard patterns (e.g. <code>foo*</code> or <code>*foo</code>) to be matched.

Any non-standard headers will be prefixed with the value specified by the <i>user defined header prefix</i> setting (default: empty string).

The strings <code>HTTP_REQUEST_HEADERS</code> and <code>HTTP_RESPONSE_HEADERS</code> will match against any of the standard HTTP request and response headers, respectively.

#### User-defined header prefix
Sets the prefix to use with user-defined (non-standard) headers.

Historically, by convention non-standard HTTP headers were prefixed with <code>X-</code> to distinguish them from the standard HTTP headers. This convention has been deprecated by the Internet Engineering Task Force (IETF) in June 2012 (RFC6648).

Default is an empty string, matching RFC6648. Use value <code>X-</code> to revert back to the pre-RFC6648 behaviour.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

