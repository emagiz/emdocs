# Basic access authentication interceptor
#### Adds basic access authentication to HTTP requests.
Client HTTP request interceptor that adds basic access authentication to HTTP requests.

This interceptor will always add header <i>Authorization</i> to the request (overwriting any existing values), as this is required for basic access authentication.

#### Username
Username to authenticate with; cannot contain a colon character.

Note that using non-ASCII characters in the username might cause problems.

<i>Required</i>

#### Password
Password to authenticate with.

Note that using non-ASCII characters in the password might cause problems.

<i>Required</i>

