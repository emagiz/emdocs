---
id: concurrent-map-cache-manager
title: Concurrent map cache manager
sidebar_label: Concurrent map cache manager
---
#### Cache manager implementation that lazily builds simple concurrent map caches.
Cache manager implementation that lazily builds concurrent map cache instances when a cache is accessed for the first time.

For more complex cache options, consider using the <i>Ehcache</i> implementation.

#### Cache manager implementation that lazily builds simple concurrent map caches.
Cache manager implementation that lazily builds concurrent map cache instances when a cache is accessed for the first time.

For more complex cache options, consider using the <i>Ehcache</i> implementation.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Allow null values
Whether to accept and convert <code>null</code> values for all caches in this cache manager, despite <code>ConcurrentHashMap</code> itself not supporting these values. (An internal holder object will be used to store user-level nulls.)

Default is <code>true</code>.

#### Store by value
Whether this cache manager stores a copy of each entry (<code>true</code>) or the reference (<code>false</code>) for all of its caches.

Default is <code>false</code>, so that the value itself is stored and no serializable contract is required on cached values.

#### Allow null values
Whether to accept and convert <code>null</code> values for all caches in this cache manager, despite <code>ConcurrentHashMap</code> itself not supporting these values. (An internal holder object will be used to store user-level nulls.)

Default is <code>true</code>.

#### Store by value
Whether this cache manager stores a copy of each entry (<code>true</code>) or the reference (<code>false</code>) for all of its caches.

Default is <code>false</code>, so that the value itself is stored and no serializable contract is required on cached values.

