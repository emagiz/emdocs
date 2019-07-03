---
id: oauth-2-0-user-redirect-required-exception-resolver
title: OAuth 2.0 user redirect required exception resolver
sidebar_label: OAuth 2.0 user redirect required exception resolver
---

Extension of <code>SimpleSoapExceptionResolver</code> that adds a <code>&lt;oauth2:redirect-url&gt;</code> element containing the redirect URL to the SOAP fault detail, in case of a <i>Spring Security OAuth 2.0</i> <code>UserRedirectRequiredException</code>.

For any other type of exception this resolver behaves exactly the same as the <code>SimpleSoapExceptionResolver</code>.

