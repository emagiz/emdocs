# Azure Storage Services authentication interceptor
#### Adds authentication for Microsoft Azure Storage Services to HTTP requests.
Client HTTP request interceptor that adds authentication for Microsoft Azure's <b>Blob, Queue, and File Services</b> (see <a href="http://msdn.microsoft.com/en-us/library/azure/dd179428.aspx" target="_blank">MSDN</a>). This component was build using <b>version 2014-02-14</b> of the Azure Storage Services specification.

The following HTTP headers are automatically included in the signature when present on the request message:
 - Content-Encoding
 - Content-Language
 - Content-Length
 - Content-MD5
 - Content-Type
 - Date
 - If-Modified-Since
 - If-Match
 - If-None-Match
 - If-Unmodified-Since
 - Range
 - All headers prefixed with "x-ms-"

If the HTTP verb of the request is <i>GET</i>, <i>HEAD</i>, <i>DELETE</i>, <i>TRACE</i> or <i>OPTIONS</i>, any <i>Content-Type</i> HTTP headers present on the request will be removed.

This interceptor will always add headers <i>x-ms-date</i> and <i>Authorization</i> to the request (overwriting any existing values), as these are required for authenticating with the Azure Storage Services.

#### Account name
Account name for Azure Storage Services, usually consisting of lower case letters and numbers only.

<i>Required</i>

#### Access key
Access key for Azure Storage Services, in Base64 string representation.

<i>Required</i>

