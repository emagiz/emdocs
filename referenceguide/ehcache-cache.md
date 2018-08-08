
Disk spool buffer size
The size (in MiB) to allocate the DiskStore for a spool buffer. Writes are made to this area and then asynchronously written to disk. Each spool buffer is used only by its cache. If you get <code>OutOfMemory</code> errors consider lowering this value. To improve DiskStore performance consider increasing it. Trace level logging in the <code>DiskStore</code> will show if put back ups are occurring. 

If not filled it defaults to <code>30</code> MiB.


Disk access stripes
Sets the number of concurrent disk access stripes (RandomAccessFiles used to access the data file). 

Default is <code>1</code>.


Disk expiry thread interval
Sets the interval in seconds between runs of the disk expiry thread. This is not the same thing as time to live or time to idle. When the thread runs it checks these settings. So this value is how often we check for expiry. 

If not filled it defaults to <code>120</code> seconds.


Name
The name of the cache.

<i>Note</i>: if you're using this cache for the eMagiz mapping service, the following named caches must exist:
- <code>emagiz_mapping_cdmCodes</code>
- <code>emagiz_mapping_systemCodes</code>
- <code>emagiz_mapping_customAttributes</code>

<i>Required</i>


Max entries local heap
Sets the maximum number of objects that will be created in the local JVM's heap memory. Value zero indicates no limit: in practice no limit means <code>Integer.MAX_SIZE (2147483647)</code>. 

This attribute and <code>max bytes local heap</code> are mutually exclusive. 

If <code>max bytes local heap</code> is not specified on the cache manager level, this attribute or <code>max bytes local heap</code>, is required and cannot be a percentage.


Max bytes local heap
Constraints the memory usage of this <i>cache</i> to use at most the specified amount of the local JVM's heap. If the cache manager's <code>max bytes local heap</code> has been defined, this cache's specified amount will be subtracted from the cache manager memory pool. Other caches will share the remainder. 

Can be specified as an absolute amount of memory, or as a percentage of the cache manager's <code>max bytes local heap</code> attribute. 

Some examples: 25%, 1073741824B, 1048576K, 1024M, 1G 

This attribute and <code>max entries local heap</code> are mutually exclusive. 

If <code>max bytes local heap</code> is not specified on the cache manager level, this attribute or <code>max entries local heap</code>, is required and cannot be a percentage.


Memory store eviction policy
The policy used to evict elements from the heap memory upon reaching the specified limit.

This can be one of:
 - <b>LRU</b>: least recently used (based on time of last access) 
 - <b>LFU</b>: less frequently used (based on number of accesses) 
 - <b>FIFO</b>: first in first out (based on time of creation)

If not filled it defaults to <code>LRU</code>.


Overflow to disk
Explicitly sets whether this Cache will overflow to disk when the in-memory cache has reached the specified limit. 

If not specified, it will default to <code>true</code> if a disk pool is specified with the <code>max bytes local disk</code> attribute on the cache and/or cache manager level, or <code>false</code> otherwise.


Max entries local disk
Sets the maximum number of objects that will be stored on disk. Value zero indicates no limit: in practice no limit means <code>Integer.MAX_SIZE (2147483647)</code>. 

This property and <code>max bytes local disk</code> are mutually exclusive. 

If <code>max bytes local disk</code> is specified on the <i>cache manager</i> level, this property cannot be used. 

If not filled it defaults to <code>0</code>.


Max bytes local disk
Constraints the disk usage of this cache to use at most the specified amount of the local disk. If the cacheManager's <code>max bytes local disk</code> attribute has been defined, this cache's specified amount will be subtracted from the cache manager disk pool. Other caches will share the remainder. 

Can be specified as an absolute amount of disk space, or as a percentage of the cache manager's <code>max bytes local disk</code> attribute. Some examples: 25%, 1073741824B, 1048576K, 1024M, 1G 

This property and <code>max entries local disk</code> are mutually exclusive. 

If the <code>max bytes local disk</code> attribute is not specified on the cache manager level, this property cannot be a percentage.


Disk persistent
Determines whether to persist the cache to disk between JVM restarts. Note that this operates independently of <code>overflow to disk</code>.

If not specified, it will default to <code>false</code>.


Eternal
Sets whether cached elements are eternal. If eternal, timeouts are ignored and elements never expire. 

Default is <code>false</code>.


Time to idle
Sets the time to idle for an element before it expires, i.e. the maximum amount of time in seconds between accesses before an element expires. Is only used if the element is not eternal. 

If not filled it defaults to <code>0</code>, which indicates that an element can idle for infinity.


Time to live
Sets the time to live for an element before it expires, i.e. the maximum amount of time in seconds between creation time and when an element expires. Is only used if the element is not eternal. 

If not filled it defaults to <code>0</code>, which indicates that an element can live for infinity.

