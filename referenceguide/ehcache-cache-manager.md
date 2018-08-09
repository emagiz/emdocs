# Ehcache cache manager
#### Cache manager based on the Ehcache project.
<a href="http://ehcache.org/documentation" target="_blank">Documentation</a>


#### Id
Name that uniquely identifies this flow component.

<i>Required</i>

#### Max bytes local heap
Constraints the total memory usage of all the caches managed by the cache manager to use at most the specified amount of the local JVM's heap. This specified amount of memory will act as a global pool for all underlying caches: any cache may reserve a specific portion of this pool, or it will be assigned a portion automatically by the cache manager. 

Can be specified as an absolute amount of memory, or as a percentage of the JVM's maximum available memory. Some examples: 25%, 1073741824B, 1048576K, 1024M, 1G 

By default no maximum is set, which disables the global JVM heap memory pool. In this case each underlying cache must specify its own maximum heap memory usage.

#### Max bytes local disk
Constraints the total disk usage of all the caches managed by the cache manager to use at most the specified amount of the local disk. This specified amount of disk space will act as a global pool for all underlying caches: any cache may reserve a specific portion of this pool, or it will be assigned a portion automatically by the cache manager. Note that these settings apply only to temporary swapping of data to disk (localTempSwap); these settings do not apply to disk persistence. 

Must be specified as an absolute amount of disk space. Some examples: 1073741824B, 1048576K, 1024M, 1G 

By default no maximum is set, which disables the global disk space pool. In this case each underlying cache may specify a maximum local disk usage, enabling the disk cache tier for that specific cache.

#### Default timeout
Default transaction timeout in seconds.

If not filled it defaults to <i>15</i> seconds.

#### Disk store path
The file system directory where any required disk files will be created. Relative paths are resolved against the eMagiz data directory.

Default is <code>ehcache</code>.

