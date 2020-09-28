Version emc 4.1.1, released 2020-09-04

First maintenance release in the eMagiz Mendix Connector 4.1.x line.

Minor changes
- Small performance improvements related to debug logging. In certain situations this could result in a higher maximum message throughput.

Bug fixes
- Sending messages synchronously from Mendix did not work when a module used a Xerces implementation other than the one provided by Mendix by default. This could cause conflicts with some Mendix App Store modules, such as the SAML module. The synchronous message flow now ignores any Xerces implementations in the userlib folder, avoiding these conflicts.