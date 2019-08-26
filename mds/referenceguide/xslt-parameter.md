---
id: xslt-parameter
title: XSLT parameter
sidebar_label: XSLT parameter
---
#### Name
Name for the XSLT parameter. Must exactly match the name specified in the <code>&lt;xsl:param name="..."/&gt;</code> section of your XSLT.

<i>Required</i>

#### Expression
Any valid SpEL expression with <code>Message</code> being the root object of the expression evaluation context. The result of this expression will be the value of this XSLT parameter.

It is also possible to reference any component in this flow using the <code>@</code> notation, e.g. <code>@'full.id.of.your.flow.component'</code>. This can be very useful for passing <i>XSLT extention gateways</i> as parameters to your XSLT.

#### Value
A simple scalar value for this XSLT parameter. You can also use property placeholders (e.g. <code>${some.value}</code>).

---
id: xslt-parameter
title: XSLT parameter
sidebar_label: XSLT parameter
---
#### Name
Name for the XSLT parameter. Must exactly match the name specified in the <code>&lt;xsl:param name="..."/&gt;</code> section of your XSLT.

<i>Required</i>

#### Expression
Any valid SpEL expression with <code>Message</code> being the root object of the expression evaluation context. The result of this expression will be the value of this XSLT parameter.

It is also possible to reference any component in this flow using the <code>@</code> notation, e.g. <code>@'full.id.of.your.flow.component'</code>. This can be very useful for passing <i>XSLT extention gateways</i> as parameters to your XSLT.

#### Value
A simple scalar value for this XSLT parameter. You can also use property placeholders (e.g. <code>${some.value}</code>).

