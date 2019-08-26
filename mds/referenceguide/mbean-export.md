---
id: mbean-export
title: MBean export
sidebar_label: MBean export
---
#### Exports message channels and message handlers as JMX MBeans.
Exports message channels and message handlers in this message flow as MBeans. This will expose management operations and monitoring metrics of those objects to JMX.

Note that message channels and message handlers do <b>not</b> collect any metrics, unless this message flow contains a <i>management</i> support object that is configured to enable those metrics.

#### Server
Defines the name of the MBeanServer bean to connect to.

Default is "mbeanServer".

#### Default domain
The domain can be left out in which case the default domain is "org.springframework.integration".

#### Managed components
Comma separated list of simple patterns for component names to register (defaults to <code>*</code>).

The pattern is applied to all components before they are registered, looking for a match on the <i>name</i> property of the <code>ObjectName</code>. A <code>MessageChannel</code> and a <code>MessageHandler</code> (for instance) can share a name because they have a different type, so in that case they would either both be included or both excluded.

A leading <code>!</code> negates the pattern match, e.g. <code>!foo*</code> means don't export components where the name matches the pattern <code>foo*</code>. For components with names that match multiple patterns, the first pattern (from left to right) wins. For example, <code>!foo*, foox</code> will match all beans that don’t start with <code>foo</code>, except <code>foox</code>.

<i>Optional</i>

#### Object name static properties
Static object properties to be used for this domain. These properties are appended to
 the ObjectName of all MBeans registered by this component.

<i>Optional</i>

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

