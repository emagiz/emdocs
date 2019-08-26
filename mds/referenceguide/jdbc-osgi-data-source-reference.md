---
id: jdbc-osgi-data-source-reference
title: JDC OSGI data source reference
sidebar_label: JDC OSGI data srouce reference
---


# JDBC OSGi data source reference
Defines a reference to a service obtained via the OSGi service registry.

This reference uniquely references the <code>javax.sql.DataSource</code> interface.



#### Interface
The service interface that the services obtained via the registry are required to support. By convention this is a Java interface type, but may also be a (non-final) class type.

####  Cardinality
Defines the required cardinality of the relationship to the backing service. If not specified, The default-cardinality attribute will apply. A value is <code>1..1</code> means that a backing service must exist (this is a mandatory service reference). A value of <code>0..1</code> indicates that it is acceptable to be no backing service (an optional service reference).

####  Bean name
Convenient shortcut for specifying a filter expression that matches on the <code>bean-name</code> property that is automatically advertised for beans published using the service element.

####  Filter
Defines an OSGi filter expression that is used to constrain the set of matching services  in the service registry. 

####  Timeout
For a <i>Reference</i> element, the amount of time (in milliseconds) to wait for a backing service to be available when an operation is invoked. If not specified, the default-timeout attribute will apply.  See also the default-timeout attribute of the osgi element.

#### Context class loader
Defines how the context class loader is managed when invoking operations on a service  backing this service reference. 

The default value is <i>Client</i> which means that the context class loader has visibility of the resources on this bundle's classpath. 
Alternate  options are <i>Service-provider</i> which means that the context class loader has visibility of  resources on the bundle classpath of the bundle that exported the service, and <i>Unmanaged</i> which does not do any management of the context class loader.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

