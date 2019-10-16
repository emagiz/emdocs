First maintenance release in the eMagiz Mendix Connector 2.4.x line.
## Minor changes
- When shutting down the Mendix App (or clicking the 'stop all' button), flows are now turned off in parallel. In apps with many flows this reduces the time needed to shutdown considerably, possibly preventing a "forced quit".
## Bug fixes
- Improved several validations for the previously released multi-select actions. Most notably, it is now possible to startup another version of the request handler. (#323534)
