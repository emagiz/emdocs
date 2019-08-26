---
id: oauth-2-0-resource
title: OAuth 2.0 resource
sidebar_label: OAuth 2.0 resource
---
#### Type
The OAuth 2.0 grant type for this resource.

For the <i>Google API</i> use <code>authorization code</code>.

<i>Required</i>

#### Client ID
This is the ID by which the resource server will identify this application.

For the <i>Google API</i>, copy this value from the <i>Google APIs Console</i>.

<i>Required</i>

#### Access token URI
The URI where the access token may be obtained.

For the <i>Google API</i>, use <code>https://accounts.google.com/o/oauth2/token</code>.

<i>Required for types <code>authorization code</code> and <code>client credentials</code></i>

#### User authorization URI
The URI to which the user will be redirected if the user is ever needed to grant an authorization code.

For the <i>Google API</i>, use <code>https://accounts.google.com/o/oauth2/auth</code>.

<i>Required for types <code>authorization code</code> and <code>implicit</code>; not allowed for type <code>client credentials</code></i>

#### Username
The username for authentication.

<i>Required for type <code>password</code>.</i>

#### Password
The password for authentication.

<i>Required for type <code>password</code>.</i>

#### Scope
Comma-separated list of strings specifying the scope of the access to the resource.

For the <i>Google API</i>, see the Google documentation for all available scopes. Some of the scopes for <i>Google Drive</i> are:
 - <code>https://www.googleapis.com/auth/drive.file</code>
 - <code>https://www.googleapis.com/auth/drive</code>
 - <code>https://www.googleapis.com/auth/drive.apps.readonly</code>
 - <code>https://www.googleapis.com/auth/drive.readonly</code>
 - <code>https://www.googleapis.com/auth/drive.readonly.metadata</code>
 - <code>https://www.googleapis.com/auth/drive.install</code>
 - <code>https://www.googleapis.com/auth/drive.appdata</code>
 - <code>https://www.googleapis.com/auth/drive.scripts</code>

Default is empty.

#### Client secret
The secret asssociated with the resource.

For the <i>Google API</i>, copy this value from the <i>Google APIs Console</i>.

Default is empty.

#### Client authentication scheme
The scheme that is used to pass the client secret.

For the <i>Google API</i>, use <code>form</code>.

Default is <code>header</code>.

#### Authentication scheme
The method for bearing the token when accessing the resource.

For the <i>Google API</i>, leave this setting on <code>header</code> (default).

Default is <code>header</code>.

#### Token name
The name of the bearer token. The default is <code>access_token</code>, which is according to the OAuth 2.0 specification, but some providers (e.g. Facebook) don't conform to the specification.

For the <i>Google API</i>, leave this value empty.

Default is <code>access_token</code>.

#### Pre-established redirect URI
Some resource servers may require a pre-established URI to which they will redirect users after users authorize an access token.

For the <i>Google API</i>, copy this value from the <i>Google APIs Console</i> (usually it is <code>urn:ietf:wg:oauth:2.0:oob</code>).

#### Use current URI
Whether the current URI should be used as a redirect (if available) rather than the registered redirect URI.

For the <i>Google API</i>, leave this setting on <code>false</code> (default).

Default is <code>false</code>.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

