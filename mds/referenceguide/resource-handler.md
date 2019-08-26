---
id: resource-handler
title: Resource handler
sidebar_label: Resource handler
---
#### Handler that looks for a matching file in the local directory to serve.
<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Handlers" target="_blank">External documentation</a>

The resource handler is passed the request first and looks for a matching file in the local directory to serve. If a file is not found, then the request is passed to the default handler which generates a 404 (or favicon.ico). 

#### Resource base
Specifies where to look for the matching files.

#### Directories listed
If set, a listing of the content of a directory is returned when that directory inside the base directory matches the received request.

#### Aliases
Set if resource aliases (eg symlink, 8.3 names, case insensitivity) are allowed.

Allowing aliases can significantly increase security vulnerabilities. 

---
id: resource-handler
title: Resource handler
sidebar_label: Resource handler
---
#### Handler that looks for a matching file in the local directory to serve.
<a href="http://wiki.eclipse.org/Jetty/Reference/Jetty_Architecture#Handlers" target="_blank">Documentation</a>

The resource handler is passed the request first and looks for a matching file in the local directory to serve. If a file is not found, then the request is passed to the default handler which generates a 404 (or favicon.ico). 

#### Resource base
Specifies where to look for the matching files.

#### Directories listed
If set, a listing of the content of a directory is returned when that directory inside the base directory matches the received request.

#### Aliases
Set if resource aliases (eg symlink, 8.3 names, case insensitivity) are allowed.

Allowing aliases can significantly increase security vulnerabilities. 

