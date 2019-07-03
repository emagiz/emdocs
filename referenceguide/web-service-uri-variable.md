---
id: web-service-uri-variable
title: Web service URI variable
sidebar_label: Web service URI variable
---
#### Name
Name of the placeholder to be replaced.

#### Expression
Expression to be evaluated to determine the replacement value.

The message is the root object of the expression, therefore the <code>payload</code> and <code>headers</code> are available directly.

Any bean may be resolved if the bean name is preceded with '@'.

