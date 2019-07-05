# OSGi service 
Exports the referenced bean as an OSGi service so it can be used by other flows.

#### Interface
Defines the interface to advertise for this service in the service registry.

####  Context class loader
Defines how the context class loader will be managed when an operation is invoked on the exported service. 

The default value is <i>Unmanaged</i> which means that no management of the context class loader is attempted. A value of <i>Service provider</i> guarantees that the context class loader will have visibility of all the resources on the class path of bundle exporting the service.

####  Auto export
Enables Spring to automatically manage the set of service interfaces advertised for the service. By default this facility is disabled. 

A value of <i>Interfaces</i> advertises all of the Java interfaces supported by the exported service. A value of <i>Class hierarchy</i> advertises all the Java classes in the hierarchy of the exported service. A value of  <i>All classes</i> advertises all Java interfaces and classes. 

####  Ranking
Specify the service ranking to be used when advertising the service.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

