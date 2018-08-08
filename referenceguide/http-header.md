
Name
Name of the message header.

<i>Required</i>


Expression
SpEL expression that is evaluated in order to determine the header value.

The evaluation context will be populated with an <code>org.springframework.http.HttpEntity</code> instance as the root object, and the following expression variables will also be made available:

<b>#requestParams</b> - a <code>MultiValueMap&lt;String, String&gt;</code> containing the request parameters from the query string or posted form data
<b>#pathVariables</b> - a <code>Map&lt;String, String&gt;</code> containing the URI path placeholders and their values
<b>#matrixVariables</b> - a <code>Map&lt;String, MultiValueMap&lt;String, String&gt;&gt;</code> containing the matrix variables according to <a href="http://docs.spring.io/spring/docs/current/spring-framework-reference/html/mvc.html#mvc-ann-matrix-variables" target="_blank">Spring MVC specification</a>
<b>#requestAttributes</b> - the <code>org.springframework.web.context.request.RequestAttributes</code> associated with the current request
<b>#requestHeaders</b> - the <code>org.springframework.http.HttpHeaders</code> object from the current request
<b>#cookies</b> - a <code>Map&lt;String, javax.servlet.http.Cookie&gt;</code> containing the cookies from the current request

<i>Required</i>

