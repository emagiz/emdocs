---
id: property-placeholder
title: Property placeholder
sidebar_label: Property placeholder
---
#### Enables the use of placeholders (${...}) for properties in this configuration.
<a href="http://docs.spring.io/spring/docs/3.1.x/spring-framework-reference/html/xsd-config.html#xsd-config-body-schemas-context-pphc" target="_blank">Documentation</a>

Activates replacement of <code>${...}</code> placeholders by registering a <code>PropertySourcesPlaceholderConfigurer</code> within the application context.

Properties will be resolved against the specified properties file or <code>Properties</code> object -- so called "local properties", if any, and against the Spring Environment's current set of <code>PropertySources</code>.

#### Properties ref.
The Java Properties object that will be used for property substitution.

If neither <i>location</i> nor <i>properties-ref</i> is specified, placeholders will be resolved against system properties.

#### Location
The location of the properties file to resolve placeholders against, as a Spring resource location: a URL, a <code>classpath:</code> pseudo URL, or a relative file path.

Multiple locations may be specified, separated by commas. If neither <i>location</i> nor <i>properties-ref</i> is specified, placeholders will be resolved against system properties.

#### File encoding
Specifies the encoding to use for parsing properties files.

Default is none, using the <code>java.util.Properties</code> default encoding.

Only applies to classic properties files, not to XML files.

#### Order
Specifies the order for this placeholder configurer. If more than one is present in a context the order can be important since the first one to be match a placeholder will win.

#### Ignore resource not found
Specifies if failure to find the property resource location should be ignored.

Default is <code>false</code>, meaning that if there is no file in the location specified an exception will be raised at runtime.

#### Ignore unresolved
Specifies if failure to find the property value to replace a key should be ignored.

Default is <code>false</code>, meaning that this placeholder configurer will raise an exception if it cannot resolve a key.

Set to <code>true</code> to allow the configurer to pass on the key to any others in the context that have not yet visited the key in question.

#### Local override
Specifies whether local properties override properties from files.

Default is <code>false</code>, meaning properties from files override local defaults.

#### Value separator
The separating character between the placeholder variable and the associated default value.

Default is <code>:</code> (colon character).

#### Trim values
Whether to trim resolved values before applying them, removing superfluous whitespace (in particular tab characters) from the beginning and end.

Default is <code>false</code>.

#### Null value
A value that should be treated as 'null' when resolved as a placeholder value, e.g. the string literal <code>null</code>.

By default, no such null value is defined.

