---
id: standard-header-enricher---custom-header
title: Standard header enricher - Custom header
sidebar_label: Standard header enricher - Custom header
---
#### Name
Name (uniquely) identifying this message header.

<i>Required</i>

#### Value
Literal value for this message header. Note that you can also use property values (<code>${...}</code>) here.

To specify a non-literal value, see the <i>expression</i> and <i>reference</i> options on the <i>advanced</i> tab.

#### Expression
SpEL expression to be evaluated at runtime to determine the header value. The evaluation context will include variables for <code>payload</code> and <code>headers</code>.

#### Reference
Reference to any bean within this configuration that will be used as the value for this header.

Note that bean references can only be used within the same message flow, i.e. sending such a header to another flow or system is usually pointless.

#### Overwrite
Whether this header value should overwrite an existing header value for the same name.

Default is <i>false</i>.

#### Type
The fully qualified class name of the header value's expected type when using <i>value</i> or <i>expression</i>.

<i>Optional</i>

---
id: standard-header-enricher---custom-header
title: Standard header enricher - Custom header
sidebar_label: Standard header enricher - Custom header
---
#### Name
Name (uniquely) identifying this message header.

<i>Required</i>

#### Value
Literal value for this message header. Note that you can also use property values (<code>${...}</code>) here.

To specify a non-literal value, see the <i>expression</i> and <i>reference</i> options on the <i>advanced</i> tab.

#### Expression
SpEL expression to be evaluated at runtime to determine the header value. The evaluation context will include variables for <code>payload</code> and <code>headers</code>.

#### Reference
Reference to any bean within this configuration that will be used as the value for this header.

Note that bean references can only be used within the same message flow, i.e. sending such a header to another flow or system is usually pointless.

#### Overwrite
Whether this header value should overwrite an existing header value for the same name.

Default is <i>false</i>.

#### Type
The fully qualified class name of the header value's expected type when using <i>value</i> or <i>expression</i>.

<i>Optional</i>

