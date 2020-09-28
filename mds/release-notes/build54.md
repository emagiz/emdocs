Release notes for build number 54
Version 54, released 2020-09-18

Small update that improves OAuth2 client support.

New features
- The 'REST template' component has a new interceptor called 'OAuth2 authorization interceptor'. This interceptor improves the user experience when configuring 'HTTP outbound gateways' and 'HTTP outbound channel adapters' to access OAuth2 protected endpoints. The new interceptor replaces the 'OAuth2 REST template', 'OAuth resource', 'OAuth2 access token advice' and the 'OAuth2 user redirect required exception resolver'. Flows that used the 'OAuth2 REST template' were migrated to use the 'REST template' with the new 'OAuth2 authorization interceptor'.

Major changes
- Added extended versions of 'default FTP session factory' and 'default FTPS session factory' that expose the 'strict reply parsing' setting. This new setting (enabled by default) can be used disable strict non-multiline parsing, as per RFC 959, section 4.2. This should not be required by a well-behaved FTP server.

Minor changes
- Updated bundle 'com.emagiz.components.security' from 6.0.0 to 7.0.0
- Updated bundle 'com.emagiz.bundles.spring-security-core' from 5.0.0.ADAPT to 5.3.4.1
- Updated bundle 'com.emagiz.bundles.spring-security-config' from 5.0.0.ADAPT to 5.3.4.1
- Updated bundle 'com.emagiz.bundles.spring-security-web' from 5.0.0.ADAPT to 5.3.4.1
- Updated bundle 'com.emagiz.bundles.spring-ws-security' from 3.0.8.1 to 3.0.8.2
- Added bundle 'com.emagiz.bundles.spring-security-oauth2-client' version 5.3.4.1
- Added bundle 'com.emagiz.bundles.spring-security-oauth2-core' version 5.3.4.1
- Removed bundle 'com.emagiz.bundles.spring-security-oauth2' 3.0.0.ADAPT
- Updated bundle 'com.emagiz.components.ftp' from 6.0.0 to 6.0.1

Bug fixes

- Fixed an issue where, only after deploying a flow containing either XSL-FO or WS-Security components, the Java XPath engine would downgrade from XPath 2.0 to XPath 1.0. If you deployed such a flow recently and still get errors related to unrecognized XPath 2.0 syntax, do a clean restart (empty 'data' and 'localrepository' directories) of the affected runtime to solve the issue. (Hotfix on September 14)