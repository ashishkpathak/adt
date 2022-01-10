# Extensions.

Add, update, and configure extensions in your Apigee organization.

Extensions enable you to integrate external resources into your API proxies. For example, you could integrate Google Cloud Platform services such as Google Cloud Storage. At run time, an API proxy uses the extension to exchange requests and responses with the external resource.

## Create Extension

Creates a new extension by configuring an instance of an installed extension and adding it to the specified organization. After you create the extension, use the Update an extension to deploy it.

```
A.D.T
Operation on Extension.
Usage: adt create extension [-hV] -e=<env> -i=<input> [-x=<hostPort>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -e, --env=<env>            The environment to create the extension in.
  -h, --help                 Show this help message and exit.
  -i, --ext-config=<input>   The create extension configuration file.
  -V, --version              Print version information and exit.
  -x, --http-proxy=<hostPort>
                             Use http proxy (host:port)
Version 1.0.1
```

### Usage

## Query Extension

Query public extension packages using the parameters to search for specific values (keywords). To get a list of all extension packages, don't specify any search values. When you get a collection, each item in the collection includes a self property with a URL to the item, including its ID. You can use that ID to retrieve details for a specific extension.
### Usage 
```
A.D.T
Operation on extension package.
Usage: adt query extension [-hV] [-c=<count>] [-d=<description>] [-k=<keywords>] [-n=<name>] [--ver=<version>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -c, --count=<count>   Response result size. Default value 25
  -d, --description=<description>
                        Value to search for in extension descriptions.
  -h, --help            Show this help message and exit.
  -k, --keywords=<keywords>
                        A comma-separated list of keywords to search for in extension keyword properties.
  -n, --name=<name>     Exact name of an extension to query for.
  -V, --version         Print version information and exit.
      --ver=<version>   The version of extension to search. Used only when name is provided.
  -x, --http-proxy=<proxyHost>
                        Host:Port of the proxy server to use.
Version 1.0.1

```

### Search by keywords 
Search by keyword 'salesforce' and return maximum of 10 results.

```
adt query extension -c 10 -k salesforce
```

### Search by name and version.
Gets the permalink for the specified extension package, given name and version.

```
adt query extension -n salesforce -v 1.0.1
```



## List Extension



### Usage

```
A.D.T
Operation on Extensions.
Usage: adt list extension [-hV] [--logs] [--name-like] [-c=<count>] -e=<env> [--id=<id>] [-n=<name>] [--token=<previousToken>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -c, --count=<count>   The number of results to return.
  -e, --env=<env>       The environment to list extensions.
  -h, --help            Show this help message and exit.
      --id=<id>         The ID of extension. The 'self' property with URL pointing to the item, includes this ID.
      --logs            List the logs for extension with ID.
  -n, --name=<name>     The exact name of the extension. Use nameLike to true for 'like' query matches.
      --name-like        True for 'like' query matches. Default false.
      --token=<previousToken>
                        Next page token retrieved from the response of previous logs request. Used for logs listing only.
  -V, --version         Print version information and exit.
  -x, --http-proxy=<proxyHost>
                        Host:Port of the proxy server to use.
Version 1.0.1

```

### List extension in an environment.

```
adt list extension -e dev
```


### List extension with a name in an environment.

```
adt list extension -e dev -n sfc-test
```

Sample response

```json
{
  "kind" : "page",
  "self" : "https://api.enterprise.apigee.com/v1/organizations/myorg/environments/dev/extensions?nameLike=sfc-test",
  "contents" : [ {
    "created" : "2021-12-16T23:28:52.507Z",
    "createdBy" : "jadmin@domain.com",
    "updated" : "2021-12-16T23:28:52.507Z",
    "updatedBy" : "jadmin@domain.com",
    "kind" : "extension",
    "self" : "https://api.enterprise.apigee.com/v1/organizations/myorg/environments/dev/extensions/cb001682-9603-4a92-3242-d30727872c03",
    "name" : "sfc-test",
    "description" : "Salesforce cloud test",
    "packageName" : "salesforce",
    "version" : "1.0.3",
    "tenant" : "myorg:dev",
    "state" : "UNDEPLOYED",
    "regions" : [ "australia-southeast1" ],
    "etag" : "ee0e748686543fc8b9f5c9a9d30a52"
  } ],
  "total" : 1,
  "totalPages" : 1,
  "pageOf" : "/extensions"
}
Exit: 0
```
### List extension with a name in an environment, matching as in SQL query 'like'

```
adt list extension -e dev -n sfc-test --name-like
```


### List extension with id in an environment

```
adt list extension -e dev --id cb001682-9603-4a92-3242-d30727872c03
```


### List logs of an extension with id in an environment

```
adt list extension -e dev --id cb001682-9603-4a92-3242-d30727872c03 --logs
```

Sample response

```json
{
  "kind" : "page",
  "contents" : [ ],
  "next" : "EAE4icn2jo39tM6oAUrxAiISIgP_G4Y4GEP-T69wDStoCCrQCSrECANSBz21qGwoMCLzP8o4GEJAvIAx9I9olvKBwY13lOf8B5vaio93OERf5KXDZ6B6wMlhCtcTclyHzC0yRdOnLqmCEAej8JyMUVoKmJb0zZYLO5F9QPrlGKwoQvk3MXz-Jr4qJBHjB1j5kAA83T9ewHZB6J4qqY3C6DClDpcP9B6b6dEYpiZYMT-D-XAsuX7oJYzO5uM_6v8FyMEecKT22rSFTMz0qN1lnCgi7kUsfB8gBldKP-7wrupqn6WkZH656rwzDZ2hA82x-LfVWhupEixtK8X2D1OAiGn16QJX7K252MfIKACoMCUgIb4jN0VYra3tFKmrhjXENHj9t2ClzQg3tqPVejf5vlMpTdg_UGqNZdy-N3CX52bdoEfs5_0_g484YpjhoeXdWAChYe82joJODRW-Xu1n_N4SFhoGCICYx44GIgwI_8bhjgYQ_5Pr3ANQ2Neh4Nn0uoSwAVIHCODms6rdF2D73ee9kP2318wDEgcIBxD7-qAAgAYIGA",
  "total" : 0,
  "totalPages" : 0
}
Exit: 0
```

## Delete Extension

Deletes all extensions in an environment or by extension id. 
### Usage

```sh
A.D.T
Operation on Extension. Deletes all extensions in an environment.
Usage: adt delete extension [-hV] -e=<environment> [-i=<id>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -e, --env=<environment>   The extension environment.
  -h, --help                Show this help message and exit.
  -i, --id=<id>             The extension id.
  -V, --version             Print version information and exit.
  -x, --http-proxy=<proxyHost>
                            Host:Port of the proxy server to use.
Version 1.0.1


Exit: 0
```
### Deletes all extensions in an environment.

```sh
adt delete extension -e dev
```


### Deletes an extension.

When you retrieve a list of extensions, each extension in the collection includes a self property with a URL to the extension, including its ID. Use that ID value in this request.

```sh
adt delete extension -e dev --id db001682-9603-4a92-3242-d30727872c03
```
