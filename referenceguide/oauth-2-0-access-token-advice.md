---
id: oauth-2-0-access-token-advice
title: OAuth 2.0 access token advice
sidebar_label: OAuth 2.0 access token advice
---
#### Copies OAuth 2.0 access tokens from message headers to the OAuth 2.0 context and vice versa.
A message handler advice implementation that reads an <i>authorization code</i> or <code>OAuth2AccessToken</code> from the request message and places it in the correct <code>OAuth2ClientContext</code> and/or <code>AccessTokenRequest</code> before the request handler is executed. This enables the specified <code>OAuth2RestTemplate</code> to be used in a message flow, instead of requiring a web application context.

This advice will also temporarily add a <code>DummyAuthentication</code> to the current security context, because the <code>OAuth2RestTemplate</code> expects to run in an authenticated (web) session.

This class uses the following two pre-defined message headers:
 - <b>emagiz_oauth2_accessToken</b>: Should contain an <code>OAuth2AccessToken</code> that is serialized, gzipped and base64-encoded to a string value. If found on the request message, this <code>OAuth2AccessToken</code> will be placed in the <code>OAuth2ClientContext</code> before executing the request handler. After executing the request handler, the current <code>OAuth2AccessToken</code> will be obtained from the <code>OAuth2ClientContext</code> and placed as a header on the reply message. 
 - <b>emagiz_oauth2_authorizationCode</b>: If found on the request message, this <i>authorization code</i> (a string) will be added to the <code>AccessTokenRequest</code> before executing the request handler. This header is ignored when a <code>OAuth2AccessToken</code> is available (see above).

#### OAuth 2.0 REST template
The <code>OAuth2RestTemplate</code> this advice will prepare the <code>OAuth2ClientContext</code> for.

The intended use is to add this advice to a request handler that in turn uses this <code>OAuth2RestTemplate</code>, like a <i>Spring Integration</i> <code>&lt;http:outbound-gateway&gt;</code> configured with a custom <code>RestTemplate</code>.

<i>Required</i>

#### Use dummy authentication
Whether this advice should use a temporary <code>DummyAuthentication</code> while executing the request handler in cases where authentication is required and hasn't been established yet.

Default is <code>true</code>.

#### Remove context from scope
Whether this advice should remove the <code>OAuth2ClientContext</code> from scope after executing the request handler. This basically clears any "session" state after each call, assuming all state information is available on the request message.

Note that this only works when the <code>OAuth2ClientContext</code> is an instance of <code>ScopedObject</code>, which usually is achieved by adding <code>&lt;aop:scoped-proxy/&gt;</code> to the bean definition. Both the eMagiz <code>&lt;emagiz:oauth2-rest-template&gt;</code> and the Spring Security OAuth <code>&lt;oauth:rest-template&gt;</code> bean definition parsers already do this implicitly.

Default is <code>true</code>.

#### Remove request from scope
Whether this advice should remove the <code>AccessTokenRequest</code> from scope after executing the request handler. This basically clears any "request" state after each call, assuming all state information is available on the request message.

Note that this only works when the <code>AccessTokenRequest</code> is an instance of <code>ScopedObject</code>, which usually is achieved by adding <code>&lt;aop:scoped-proxy/&gt;</code> to the bean definition. Both the eMagiz <code>&lt;emagiz:oauth2-rest-template&gt;</code> and the Spring Security OAuth <code>&lt;oauth:rest-template&gt;</code> bean definition parsers already do this implicitly.

Default is <code>true</code>.


Additional request parameters that will be added to any <code>UserRedirectRequiredException</code> that occurs while executing the request handler.

For example, when using the <i>Google API</i> you might want to add the parameters <code>"access_type=offline"</code> and <code>"approval_prompt=auto"</code> to the redirect URL.

Note that any parameter specified this way might overwrite an existing parameter, so you should probably not use any of the OAuth 2.0 default parameters (e.g. <code>client_id</code>, <code>redirect_uri</code>, <code>response_type</code>, <code>scope</code>).

Default is empty.

