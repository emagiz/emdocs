---
id: mail-header-enricher---cc
title: Mail header enricher - Cc
sidebar_label: Mail header enricher - Cc
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

