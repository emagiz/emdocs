First maintenance release in the eMagiz Mendix Connector 2.2.x line.
## Bug fixes
- Solved a problem where asynchronous entry connectors could fail to acknowledge the successful delivery of a message. In extremely high load environments where the same entry connector would be called multiple times concurrently, this could lead to errors and possibly duplicate messages.
