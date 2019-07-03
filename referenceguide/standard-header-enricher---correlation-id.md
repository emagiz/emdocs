---
id: standard-header-enricher---correlation-id
title: Standard header enricher - Correlation id
sidebar_label: Standard header enricher - Correlation id
---
#### Expression
SpEL (Spring Expression Language) expression that computes the value.

Example:
"payload.toUpperCase() + '_US' "

See also: 
<a href="http://static.springsource.org/spring/docs/3.0.x/reference/expressions.html" target="_blank>SpEL documentation</a>

#### Overwrite
Boolean value to indicate whether this header value should overwrite an existing header value for the same name.

Default is 'false'.

