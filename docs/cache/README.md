# CACHE
## CREATE CACHE
Creates a cache in an environment. Caches are created per environment. For data segregation, a cache created in 'test', for example, cannot be accessed by API proxies deployed in 'prod'. To create a cache with the default settings, pass an empty request body.

### USAGE

```sh
adt create cache --help
```

```sh
Operation on App.
```

#### Import a cache config.

Import a cache configuration stored on local machine as following directory structure.


```sh
adt create cache -n <cache-name> -e test --cache-config <cache-config-location>
```

Example

```sh
adt create cache -n http-cache -e test --cache-config ../http-cache/http-cache.json
```

  The structure of api-httpbin-proxy as an example is

```sh
├──http-cache
│   └── http-cache.json
```

Sample http-cache.json 

```json
{
  "description": "My cache",
  "diskSizeInMB": 0,
  "distributed": true,
  "expirySettings": {
    "expiryDate": {
      "value": "09-18-2021"
    },
    "valuesNull": "true"
  },
  "inMemorySizeInKB": 0,
  "maxElementsInMemory": 0,
  "maxElementsOnDisk": 0,
  "name": "mycache",
  "overflowToDisk": false,
  "persistent": false,
  "skipCacheIfElementSizeInKBExceeds": 1000
}
```

## List a Cache

Lists all caches in an environment.

```sh
adt list cache -e <env>
```

Lists a cache in an environment.

```sh
adt list cache -n <cache-name> -e <env>
```


## UPDATE Cache
Updates a cache in an environment. You must specify the complete definition of the cache, including the properties that you want to change and the ones that retain their current value. Any properties omitted from the request body are reset to their default value. Get information about the cache to view the current value of all properties, then pass the full set and change only those that you want to update.

```sh
adt update cache -n <cache-name> -e <env> --cache-config <config-location>
```


## DELETE Cache
Deletes a cache.

```sh
adt delete cache -n <cache-name> -e <env> 
```



## Clear Cache 

Clears all cache entries.

```sh
adt delete cache -n <cache-name> -e <env> --all-keys
```

### Clear Cache Entry
Clears a cache entry, which is identified by the full CacheKey prefix and value. For more on cache keys, see [Working with cache keys](https://docs.apigee.com/api-platform/reference/policies/working-cachekeys).

To learn how to clear a cache using policies, see Example: General purpose caching.

To use the API call, specify the complete CacheKey (any Prefix and KeyFragments) and the value of the entry that you want to clear.

For example, for the following Cache entry:

```text
apifactory__test__cacheforecast__8__default__12797282
```

Clear the cache entry with env <test>.

CacheKey is specified in the Cache or ResponseCache policy responsible for interacting with the specified Cache resource.

```sh
adt delete cache -n <cache-name> -e <env> --key <key>
```

Example:
```sh
adt delete cache -n http-cache -e test -k apifactory__test__cacheforecast__8__default__12797282
```