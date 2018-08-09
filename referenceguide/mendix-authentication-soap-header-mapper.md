# Mendix authentication SOAP header mapper
#### Maps Mendix authentication credentials to/from web service SOAP headers.
<code>SoapHeaderMapper</code> implementation that maps Mendix web service authentication SOAP headers to/from the <i>emagiz_ws_mxauth</i> message header. This mapping is only performed on request messages, as reply message don't contain authentication data.

The intended use for this header mapper is for 'proxying' authentication credentials from a web service hosted by eMagiz to a Mendix web service. Note that this does not provide an actual authentication mechanism to the eMagiz web service.

The source authentication SOAP header should have the following layout:
<pre>
&lt;exam:authentication xmlns:exam="http://www.example.org/"&gt;
  &lt;exam:username&gt;username&lt;/exam:username&gt;
  &lt;exam:password&gt;password&lt;/exam:password&gt;
&lt;/exam:authentication&gt;
</pre>
 
The three XML-elements in the example above can have any name and namespace, but the structure must be the same.
The target SOAP header that is send to Mendix will always look the same (this is a fixed layout defined by Mendix); only the namespace is configurable.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Source authentication QName
Qualified name for the <i>authentication</i> SOAP header element of the inbound SOAP request message, e.g. <code>{http://www.example.org/}authentication</code>.

Can be specified using any of the following syntax options:
 - <code>localPart</code>
 - <code>{namespace}localPart</code>
 - <code>{namespace}prefix:localPart</code>

#### Source username QName
Qualified name for the <i>username</i> element in the <i>authentication</i> SOAP header element of the inbound SOAP request message, e.g. <code>{http://www.example.org/}username</code>.

Can be specified using any of the following syntax options:
 - <code>localPart</code>
 - <code>{namespace}localPart</code>
 - <code>{namespace}prefix:localPart</code>

#### Source password QName
Qualified name for the <i>password</i> element in the <i>authentication</i> SOAP header element of the inbound SOAP request message, e.g. <code>{http://www.example.org/}password</code>.

Can be specified using any of the following syntax options:
 - <code>localPart</code>
 - <code>{namespace}localPart</code>
 - <code>{namespace}prefix:localPart</code>

#### Target namespace
Namespace for the Mendix <i>authentication</i> SOAP header element of the outbound SOAP request message, e.g. <code>http://www.example.com/</code>.

#### Throw exception inbound
Whether to throw a <code>SoapHeaderException</code> if the inbound SOAP request message is missing any of the required authentication data in the SOAP header.

Default is <code>true</code>, which guarantees that all generated request messages will contain the <i>emagiz_ws_mxauth</i> message header. Disabling this will result in messages being created without this header (these cases are also logged as warnings).

#### Throw exception outbound
Whether to throw a <code>SoapHeaderException</code> if the outbound request message is missing the required <i>emagiz_ws_mxauth</i> message header (or if the header value is incorrect).

Default is <code>true</code>, which guarantees that all generated request SOAP messages will contain the Mendix authentication SOAP header. Disabling this will result in messages being created without this header (these cases are also logged as warnings).

