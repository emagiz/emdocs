---
id: complex-soap-header-mapper
title: Complex SOAP header mapper
sidebar_label: Complex SOAP header mapper
---

SpEL expression that will be used to fill the outgoing SOAP header of consumed web service requests and published web service responses.

<i>Optional</i> ; if empty, this header mapper will not add a SOAP header to outgoing web service requests or responses.

<b>Example SpEL expression:</b>
<pre>
'&lt;erp:authentication xmlns:erp="http://www.example.com/ns/erp/1.0/"&gt;
  &lt;erp:user&gt;' + erp_user + '&lt;/erp:user&gt;
  &lt;erp:passphrase&gt;' + erp_passphrase + '&lt;/erp:passphrase&gt;
&lt;/erp:authentication&gt;'
</pre>
Note that the root object of the SpEL evaluation context is always the message's header, so <code>erp_user</code> in the above example will be replaced with the value of the <code>erp_user</code> message header.

Also note that it's possible to use <code>${}</code> property placeholders in this SpEL expression. These placeholders will be resolved first, before the SpEL expression is evaluated.


Mapping between header names and XPath expressions to determine the header values when processing the incoming SOAP header of consumed web service responses and published web service requests.

<i>Optional</i> ; if empty, this header mapper will not process the SOAP header of incoming web service requests or responses.

<b>Example XPath expressions:</b>
<pre>
erp_user       -> erp:authentication/erp:user
erp_passphrase -> erp:authentication/erp:passphrase
</pre>
Note that the root XML node of the XPath evaluation context is always the <code>&lt;soap:Header&gt;</code> element, so the above example is the exact reverse of the SpEL expression example (provided that the <code>erp</code> namespace prefix is correctly specified).

Also note that the XPath expression is always evaluated as a string value: if the resulting string is empty, the message header is not added to the message.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

---
id: complex-soap-header-mapper
title: Complex SOAP header mapper
sidebar_label: Complex SOAP header mapper
---

SpEL expression that will be used to fill the outgoing SOAP header of consumed web service requests and published web service responses.

<i>Optional</i> ; if empty, this header mapper will not add a SOAP header to outgoing web service requests or responses.

<b>Example SpEL expression:</b>
<pre>
'&lt;erp:authentication xmlns:erp="http://www.example.com/ns/erp/1.0/"&gt;
  &lt;erp:user&gt;' + erp_user + '&lt;/erp:user&gt;
  &lt;erp:passphrase&gt;' + erp_passphrase + '&lt;/erp:passphrase&gt;
&lt;/erp:authentication&gt;'
</pre>
Note that the root object of the SpEL evaluation context is always the message's header, so <code>erp_user</code> in the above example will be replaced with the value of the <code>erp_user</code> message header.

Also note that it's possible to use <code>${}</code> property placeholders in this SpEL expression. These placeholders will be resolved first, before the SpEL expression is evaluated.


Mapping between header names and XPath expressions to determine the header values when processing the incoming SOAP header of consumed web service responses and published web service requests.

<i>Optional</i> ; if empty, this header mapper will not process the SOAP header of incoming web service requests or responses.

<b>Example XPath expressions:</b>
<pre>
erp_user       -> erp:authentication/erp:user
erp_passphrase -> erp:authentication/erp:passphrase
</pre>
Note that the root XML node of the XPath evaluation context is always the <code>&lt;soap:Header&gt;</code> element, so the above example is the exact reverse of the SpEL expression example (provided that the <code>erp</code> namespace prefix is correctly specified).

Also note that the XPath expression is always evaluated as a string value: if the resulting string is empty, the message header is not added to the message.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

