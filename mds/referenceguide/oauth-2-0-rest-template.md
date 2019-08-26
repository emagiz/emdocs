---
id: oauth-2-0-rest-template
title: OAuth 2.0 REST template
sidebar_label: OAuth 2.0 REST template
---
#### Provides client-side OAuth 2.0 support to HTTP (REST) request.
REST template that is able to make OAuth 2.0 authenticated REST requests with the credentials of the provided resource.

This <i>eMagiz</i> version of <code>OAuth2RestTemplate</code> uses scope <code>"thread"</code> instead of the scopes <code>"session"</code> and <code>"request"</code> used by the standard <i>Spring Security OAuth</i> version. This enables the <code>OAuth2RestTemplate</code> to run without a web application context. See also <i>OAuth 2.0 access token advice</i> on how to integrate this with a <i>Spring Integration</i> message flow.

#### Resource
The <i>OAuth 2.0 resource</i> governing the configuration of this client.

<i>Required</i>

#### Retry bad access tokens
Whether a request that has an existing access token and which then leads to an <code>AccessTokenRequiredException</code> should be retried (immediately, once). Useful if the remote server doesn't recognize an old token which is stored in the client, but is happy to re-grant it.

Default is <code>true</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: oauth-2-0-rest-template
title: OAuth 2.0 REST template
sidebar_label: OAuth 2.0 REST template
---
#### Provides client-side OAuth 2.0 support to HTTP (REST) request.
REST template that is able to make OAuth 2.0 authenticated REST requests with the credentials of the provided resource.

This <i>eMagiz</i> version of <code>OAuth2RestTemplate</code> uses scope <code>"thread"</code> instead of the scopes <code>"session"</code> and <code>"request"</code> used by the standard <i>Spring Security OAuth</i> version. This enables the <code>OAuth2RestTemplate</code> to run without a web application context. See also <i>OAuth 2.0 access token advice</i> on how to integrate this with a <i>Spring Integration</i> message flow.

#### Resource
The <i>OAuth 2.0 resource</i> governing the configuration of this client.

<i>Required</i>

#### Retry bad access tokens
Whether a request that has an existing access token and which then leads to an <code>AccessTokenRequiredException</code> should be retried (immediately, once). Useful if the remote server doesn't recognize an old token which is stored in the client, but is happy to re-grant it.

Default is <code>true</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

