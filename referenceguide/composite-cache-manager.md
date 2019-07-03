---
id: composite-cache-manager
title: Composite cache manager
sidebar_label: Composite cache manager
---
#### Cache manager implementation that delegates to a list of other cache managers.
Composite cache manager implementation that iterates over a list of cache manager instances.

Allows a no-op cache manager to be automatically added to the list for handling the cache declarations without a backing store.

#### Fallback to no-op cache
Indicate whether a no-op cache manager should be added at the end of the manager lists. In this case, cache requests not handled by the configured cache managers will be automatically handled by the no-op cache manager (which simply accepts any item without actually caching it).

Default is <code>false</code>.


The cache managers that this composite cache manager delegates to. Upon a cache request, the cache managers are searched in the specified order.

Note that if you specify a cache manager in this list that is capable of <b>dynamic cache</b> creation (for example, a <i>concurrent map cache manager</i>), you should put it at the end of the list. Otherwise, some of the other specified cache managers will never be used at all.

#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

