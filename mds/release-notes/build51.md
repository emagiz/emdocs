Release notes for build number 51
Version 51, released 2020-07-10

Small update that fixes two REST specific issues.
Minor changes
Updated bundle 'com.emagiz.components.http' from 7.0.0 to 7.0.1
Updated bundle 'com.emagiz.osgi.extender.jms' from 2.0.0 to 2.0.1
Bug fixes
Custom REST templates configured to use an Apache HttpComponents request factory caused errors during deployment if the (optional) connect and read timeout settings were left empty.
Response messages of a HTTP outbound gateway have a message header called 'http_statusCode' of Java type 'o.s.http.HttpStatus'. When sending such messages to a JMS queue, this header value was "flattened" to a String value. Before build number 50 this would result in Strings such as "200" or "404", but build number 50 changed this to Strings like "200 OK" or "404 Not Found". This would cause issues if a downstream HTTP inbound gateway would try to parse and use this status code for its responses. To fix this, these header values are now "flattened" to an Integer value (such as 200 or 404) instead.