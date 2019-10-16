Important update to avoid downstream out-of-memory issues with large messages.
## Major changes
- There is now a upper limit on the size of log, error, and debug messages, to prevent out-of-memory issues when processing very large messages.
- The Java, Karaf and eMagiz version numbers are now logged during startup of a runtime and are visible on the iPaaS log entries page. This feature is automatically available for (infra) flows from build number 28 onwards.
## Minor changes
- The eMagiz XPath functions (such as 'ezx:format-dateTime') now also work outside of XSLTs, for example in the XPath header enricher.
