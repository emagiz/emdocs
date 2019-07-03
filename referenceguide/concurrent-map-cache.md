---
id: concurrent-map-cache
title: Concurrent map cache
sidebar_label: Concurrent map cache
---
#### Simple cache implementation useful for testing or simple caching scenarios.
Simple cache implementation based on the core Java <code>java.util.concurrent</code> package.

Useful for testing or simple caching scenarios; for more complex caching scenarios, consider using the <i>Ehcache</i> implementation.

#### Allow null values
Whether to allow <code>null</code> values (adapting them to an internal null holder value).

Default is <code>true</code>.

#### Name
The name of the cache.

<i>Note</i>: if you're using this cache for the eMagiz mapping service, the following named caches must exist:
- <code>emagiz_mapping_cdmCodes</code>
- <code>emagiz_mapping_systemCodes</code>
- <code>emagiz_mapping_customAttributes</code>

<i>Required</i>

