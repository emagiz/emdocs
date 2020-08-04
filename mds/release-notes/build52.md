Release notes for build number 52
Version 52, released 2020-07-24

Small update that adds OData support to the eMagiz runtime.
New features
Flows can now expose OData 4.01 endpoints, using the new 'simple OData servlet' option (located in the Jetty server support object) in combination with new component 'simple OData storage gateway'. Nearly all read operations as defined in the specification are implemented; data modification is not yet supported.
Minor changes
Added bundle 'com.emagiz.bundles.olingo' 4.7.1.1
Added bundle 'com.emagiz.components.odata' 1.0.0
Added bundle 'org.locationtech.jts.jts-core' 1.17.0
Updated bundle 'com.emagiz.bundles.groovy-all' from 2.5.8.1 to 2.5.13.1
Bug fixes
Fixed error "Unable to load FastStringService" when parsing JSON in Groovy scripts.