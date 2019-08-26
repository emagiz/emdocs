---
id: http-request-address-extracting-interceptor
title: HTTP request address extracting interceptor
sidebar_label: HTTP request address extracting interceptor
---
#### Interceptor that extracts the remote and local IP address & port and "X-Forwarded-For" header from the incoming HTTP request.
<code>EndpointInterceptor</code> that extracts the remote and local IP address & port and the <i>X-Forwarded-For</i> HTTP header from each incoming <code>HttpServletRequest</code>, and stores them as properties in the <code>MessageContext</code> before the endpoint is invoked.

The properties added by this interceptor have the following names:
 - <code>emagiz_ws_remoteAddress</code>
 - <code>emagiz_ws_remotePort</code>
 - <code>emagiz_ws_localAddress</code>
 - <code>emagiz_ws_localPort</code>
 - <code>emagiz_ws_forwardedFor</code> <i>(present only if the request contains the "X-Forwarded-For" HTTP header)</i>

The intended use of this interceptor is to prepare the <code>MessageContext</code> for the <i>Spring Integration Web Service Inbound Gateway</i> (a <code>MessageEndpoint</code> implementation), so it will add the remote and local IP address and port as message headers when constructing the resulting Spring Integration message. These message headers will have the same names as stated above.

