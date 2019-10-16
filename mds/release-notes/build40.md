Small update that fixes a specific mail issue.
## Minor changes
- Added bundle 'com.emagiz.osgi.mimetypes' 1.0.0
## Bug fixes
- Fixed an issue where sending simple plain e-mails would fail with "javax.activation.UnsupportedDataTypeException: text/plain" errors.
## Known issues
- Deploying a flow with this build number on older runtimes (before version 4.2.0 released on 2017-11-16) did not work. This has been corrected on 2019-06-03: if you encountered this issue, clear the 'localrepository' folder of the runtime and try installing the flow again. Or, better yet, update the runtime to the latest version.
