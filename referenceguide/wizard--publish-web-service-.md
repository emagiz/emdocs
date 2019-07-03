---
id: wizard--publish-web-service-
title: Wizard 'publish web service'
sidebar_label: Wizard 'publish web service'
---
#### Host
Host name the generated Jetty web server will listen on for web service requests, e.g. <code>myserver.mydomain.com</code>.

Leave empty to listen on all available host names (this usually includes at least <code>localhost</code>).

#### Port
The port number the generated Jetty web server will listen on for web service requests.

Port <code>80</code> is the default HTTP port, but if this port is already in use by another application on the server, you'd have to specify another (unused) port number.

#### Web service name
Name of this web service, used for creating the URL to host the web service on.

Should be a short but descriptive term, e.g. <code>example-service</code>.

#### Web service URL
The full URL the web service will be hosted on.

If the <i>host</i> field is left empty the value <code>localhost</code> is used in this URL, but (depending on the setup of your network) other host names will work as well.

#### Expose WSDL?
Whether you want to expose the WSDL for this web service to the outside world.

For security reasons it might be a good idea to <b>not</b> expose the WSDL, but in this case you'd have to provide the WSDL to others in some other way (e.g. e-mail it to them).

#### WSDL resource
The full path to the WSDL document to expose, e.g. <code>resources/example-service.wsdl</code>.

#### WSDL URL
The full URL where the WSDL of this web service will be hosted on.

If the <i>host</i> field is left empty the value <code>localhost</code> is used in this URL, but (depending on the setup of your network) other host names will work as well.

#### Expose XSD?
Whether you want to expose the XSD for this web service to the outside world.

For security reasons it might be a good idea to <b>not</b> expose the XSD, but in this case you'd have to provide the XSD to others in some other way (e.g. e-mail it to them).

Note that if you are exposing an auto-generated WSDL, this WSDL will already contain the full XSD contents. 

#### Validate requests?
Whether to validate incoming web service requests against an XSD or not.

If enabled, when an incoming request is invalid, a SOAP fault containing the validation errors is automatically send back as the response.

If disabled, all requests (valid and invalid) are passed through.

#### Validate responses?
Whether to validate outgoing web service responses against an XSD or not.

#### XSD resource
The full path to the XSD document to use, e.g. <code>resources/example-service.wsdl</code> or <code>classpath:com/emagiz/components/mail/emagiz-mail-1.0.xsd</code>.

#### XSD URL
The full URL where the XSD of this web service will be hosted on.

If the <i>host</i> field is left empty the value <code>localhost</code> is used in this URL, but (depending on the setup of your network) other host names will work as well.

