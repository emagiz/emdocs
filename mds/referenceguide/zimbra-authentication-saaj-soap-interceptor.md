---
id: zimbra-authentication-saaj-soap-interceptor
title: Zimbra authentication SAAJ SOAP interceptor
sidebar_label: Zimbra authentication SAAJ SOAP interceptor
---
#### Adds authentication information for calling a Zimbra web service.
ClientInterceptor implementation that adds the required authentication information for calling a Zimbra web service to request messages. 

Only messages of type SaajSoapMessage are supported by this class. 

Because Zimbra uses authentication tokens, this interceptor works as follows: 
 * If a non-expired authentication token is cached, that token is added to the request message. 
 * Otherwise, an authentication request is send to the specified URI using the given username and password. 
 * The response to this request is expected to contain a new authentication token, which is added to the request message. 
 * Depending on the lifetime correction (see setLifetimeCorrection(long)), this token is cached for a certain amount of time. 

#### Authentication URI
URI of the Zimbra web service that handles <AuthRequest> messages and returns authentication tokens

#### Username
User name of the Zimbra user account

#### Password
Password of the Zimbra user account

#### Lifetime correction
After the lifetime of an authentication token has expired a new authentication request is made, resulting in token that is cached for the duration of the lifetime.

With this method you can influence this caching behaviour by adding a correction to this lifetime: 
 * A non-positive value (zero or less) is added to the lifetime value returned in the authentication response, basically shortening that lifetime (for example, to account for clock differences). Setting the correction to a very large negative number effectively will disable all caching. 
 * A positive value (one or more) is used as the lifetime value, ignoring the value returned in the authentication response (unless the value specified exceeds this value, in which case the unmodified returned lifetime value is used). 
Default is -300000L, which will subtract 5 minutes from the token lifetime returned in the authentication response.

#### Message factory
The message factory used for creating authentication request messages.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

