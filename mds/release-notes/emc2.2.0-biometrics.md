Update adding two (advanced) configuration options to the eMagiz Mendix Connector.
## Minor changes
- The receive timeout for replies of synchronous flows is now configurable. The default is 20 seconds (which is the same value as was being used previously), but you can increase or decrease this timeout if required.
- The number of concurrent consumers (initial, maximum and idle limit) is now configurable on each exit connector. The default is 1 concurrent consumer (which is the same value as was being used previously), but you can increase this limit if required.
