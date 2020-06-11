First maintenance release in the eMagiz Mendix Connector 4.0.x line.

Bug fixes
- The import mapping in the message listeners did not work when a module uses a Xerces implementation other than the one provided by Mendix by default. This could cause conflicts with some Mendix App Store modules. The message listeners now ignore the Xerces implementation in the userlib folder.