---
id: xpath-header-enricher---header
title: XPath header enricher - Header
sidebar_label: XPath header enricher - Header
---
#### Specifies a header element by its name and an XPath expression
The value of the header is specified by the result of the XPath expression.

#### Name
The name of the header to be enriched.

#### XPath expression
Reference to an XPath expression that is used for calculating the header value.

The XPath expression is a support object that you can add to the flow, so it can be reused across flow components.

#### Overwrite
Boolean value to indicate whether this header value should overwrite an existing header value for the same name.

Default is 'false'.

#### Evaluation type
The result type expected from the XPath evaluation. This will be the type of the header value.

Default is 'STRING_RESULT'.

#### Header type
The fully qualified class name of the header value's expected type.

