# DATA MASK

Filter data from trace sessions.
Apigee Edge enables developers to capture message content to enable runtime debugging of APIs calls. In many cases, API traffic contains sensitive data, such as credit cards or personally identifiable health information (PHI) that needs to filtered out of the captured message content. Mask configurations enable you to specify data that will be filtered out of trace sessions. Masking configurations can be set globally (at the organization-level) or locally (at the API proxy level).

Create a data-mask using the methods described below.

### USAGE

```sh
$ adt create data-mask -h
```

Sample response

```sh
A.D.T
Operation on Data Masks.
Usage: adt create data-mask [-hV] [-a=<apiName>] -i=<dataMaskConfig> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -a, --api-name=<apiName>   The API proxy name. Optional. If not provided datamask would be created at organization level.
  -h, --help                 Show this help message and exit.
  -i, --datamask-config=<dataMaskConfig>
                             The data-mask config location.
  -V, --version              Print version information and exit.
  -x, --http-proxy=<proxyHost>
                             Host:Port of the proxy server to use.
Version 1.3.0


Exit: 0
```

Create a data-mask for organization, using the dm.json as datamask config.

```sh
$ adt create data-mask -i /tmp/dm.json
```

Create a data-mask for an API (api-name), using dm.json as datamask config.

```sh
$ adt create data-mask -a api-name -i /tmp
```


## LIST DATA MASKS


### USAGE

```sh
$ adt list data-mask  -h
```

Sample response

```sh
A.D.T
Operation on datamask.
Usage: adt list data-mask [-hoV] [-a=<apiName>] [-n=<maskName>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -a, --api-proxy=<apiName>
                  The API Proxy for which datamask was created.
  -h, --help      Show this help message and exit.
  -n, --mask-config-name=<maskName>
                  Gets the details for a data mask defined for an API proxy, if -a API proxy name provided, else for an organization.
  -o, --org       Lists data masks defined for an organization.
  -V, --version   Print version information and exit.
  -x, --http-proxy=<proxyHost>
                  Host:Port of the proxy server to use.
Version 1.3.0

```


Lists data-masks for an organization.

```sh
$ adt list data-mask
```

Sample response

```sh
[ "default" ]
Exit: 0

```


Lists data-masks for an API proxy.

### USAGE
```sh
adt list data-mask -a api-proxy-name
```

Sample response

```sh
[ "default" ]
Exit: 0

```

Gets an datamask definition for an organziation.

### USAGE

```sh
adt list data-mask -n <maskconfig> --org
```

Sample response

```sh

{
  "name" : "default",
  "variables" : [ "request.formparam.password" ]
}
Exit: 0

```

Gets an datamask definition <maskconfig> for an API <api-proxy-name>.

```sh
adt list data-mask -n <maskconfig> -a <api-proxy-name>.
```

Sample response
```sh
{
  "name" : "default",
  "variables" : [ "request.formparam.password" ]
}
Exit: 0
```

## DELETE DATA MASK


### USAGE

```sh
adt delete data-mask --help
```

Sample response

```sh
A.D.T
Operation on data mask.
Usage: adt delete data-mask [-hV] [-a=<apiName>] -n=<maskName> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -a, --api-proxy=<apiName>
                  The API Proxy for which datamask to be deleted. If not defined, it would delete the one defined at organization level, if any.
  -h, --help      Show this help message and exit.
  -n, --mask-config-name=<maskName>
                  The datamask name to delete. Usually its 'default'.
  -V, --version   Print version information and exit.
  -x, --http-proxy=<proxyHost>
                  Host:Port of the proxy server to use.
Version 1.3.0


Exit: 0
```

Delete datamask 'default' from the organization.

```sh
adt delete data-mask -n default
```

Delete datamask 'default' from API proxy api-name.

```sh
adt delete data-mask -n default -a api-name
```
