---
id: metacom-authentication-saaj-soap-interceptor
title: Metacom authentication SAAJ SOAP interceptor
sidebar_label: Metacom authentication SAAJ SOAP interceptor
---
#### Interceptor that adds the required authentication information for calling a Metacom web service. 
Adds the required authentication information for calling a Metacom web service.

Only messages of type <code>SaajSoapMessage</code> are supported by this class. 

Because Metacom uses session IDs, this interceptor works as follows:

* If a non-expired (or static) session ID is cached, that SID is added to the request message (see note below).
* Otherwise, a login request is send to the specified URI using the given username and password (and optionally the given application).
* The response to this request is expected to contain a new session ID, which is added to the request message (see note below).
* Depending on the specified lifetime, this SID is cached for a certain amount of time (static SIDs ignore this lifetime).

Note that a single empty <code>&lt;SID/&gt;</code> element (namespace and case are ignored) is required as one of the child elements of the root element of the request message, because this is where the actual SID is inserted. If the request message doesn't contain exactly one root element or this root element doesn't contain exactly one empty <code>&lt;SID/&gt;</code> element, an exception is thrown.

#### Authentication method
Metacom authentication method to use.

<b>Login application</b>: Uses the Metacom <i>loginapplication</i> web service operation for obtaining SIDs. Not available in older Metacom versions.
<b>Login</b>: Uses the Metacom <i>login</i> web service operation for obtaining SIDs. Deprecated in newer Metacom versions.
<b>Static SID</b>: Uses a static, pre-defined SID.

#### Authentication URI
URI of the Metacom web service that handles <code>&lt;login&gt;</code> or <code>&lt;loginapplication&gt;</code> messages and returns session IDs.

<i>Required</i>

#### Login
Login (username) to use for authenticating with Metacom.

<i>Required</i>

#### Password
Password to use for authenticating with Metacom.

<i>Required</i>

#### Application
Application to use for authenticating with Metacom.

<i>Required</i>

#### Lifetime
After the lifetime (in milliseconds) of a session ID has expired a new login request is made, resulting in SIDs being cached for the duration of their lifetime. 

Setting the lifetime to zero or less basically disables all SID caching. Setting the lifetime to a value that is higher than the actual duration of the sessions in Metacom will result in authentication failures, so try to find the right balance between better performance (higher values for lifetime) and less chance of authentication errors (lower values). 

Default is <code>0</code>, which disables SID caching.

#### Static SID
The static SID to use for authenticating with Metacom.

<i>Required</i>

#### Message factory
The message factory used for creating login request messages.

<i>Optional</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

