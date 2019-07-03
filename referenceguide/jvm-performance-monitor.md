---
id: jvm-performance-monitor
title: JVM performance monitor
sidebar_label: JVM performance monitor
---
#### Factory class for creating a PerformanceMonitor and registering it as an MBean with the MBean server. 
Factory class for creating a PerformanceMonitor and registering it as an MBean with the MBean server. 

Requires a license for the monitoring module.

#### MBean server
The MBeanServer the MBean will be registered with. 

Default is the locally running MBean server as returned by JmxUtils.locateMBeanServer().

This method can only be called if the the MBean is not registered.

#### Domain
The domain in which the MBean will be registered. 

Default is 'com.emagiz'.

This method can only be called if the the MBean is not registered.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

