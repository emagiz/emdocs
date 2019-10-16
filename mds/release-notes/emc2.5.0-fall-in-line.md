Update adding configurable timeout settings to exit connectors and other minor changes.
## New features
- When an exit connector flow delivers a message to a Mendix web service, the connect and read timeouts are now configurable.
## Minor changes
- Maximum size of error messages is now limited, identical to how other eMagiz runtimes truncate them. This prevents huge messages that cannot be delivered from causing out-of-memory exceptions during error handling.
- Message headers that could cause deserialization issues on the receiving end are now converted to (safe) string representations, identical to how other eMagiz runtimes handle them.
