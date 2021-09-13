# API PROXY
## CREATE API PROXY
Creates an API Proxy using one of the methods described below. The API proxy created will not be accessible at runtime until it is deployed to an environment.



### USAGE

```sh
adt create apiproxy --help
```

```sh
Operation on API Proxy.
Usage: adt create apiproxy [-dhV] [-e=<env>] -n=<name> [-p=<input>]
                           [-x=<hostPort>]
  -d, --deploy              Optionally deploy the proxy.
  -e, --env=<env>           Environment to deploy into.
  -h, --help                Show this help message and exit.
  -n, --api-name=<name>     The name of API proxy.
  -p, --proxy-dir=<input>   Location of apiproxy directory or bundled proxy zip
                              file.
  -V, --version             Print version information and exit.
  -x, --http-proxy=<hostPort>
                            Use http proxy (host:port)
```                            
  
Note: Proxies using the create command, get created by not deployed. To create and deploy proxies, refer to below documentation.

#### Import an API Proxy directory.

Import an API proxy configuration stored on local machine as following directory structure.


```sh
adt create apiproxy -n <api-proxy-name> --proxy-dir <proxy-location>
```

Example

```sh
adt create apiproxy -n api-httpbin-proxy --proxy-dir ../api-httpbin-proxy/
```

  The structure of api-httpbin-proxy as an example is

```sh
├── api-httpbin-v1
│   └── apiproxy
│       ├── api-httpbin-v1.xml
│       ├── policies
│       ├── proxies
│       │   └── default.xml
│       └── targets
│           └── default.xml
```

#### Import a zipped bundle

Import an API proxy bundle stored as a zip file on your local machine to your organization on Edge by doing the following.

```sh
adt create apiproxy -n api-httpbin-proxy --proxy-dir ../api-httpbin-proxy.zip
```

NOTE: ADT can take **relative** and **absolute** paths.

Optionally the created proxy can be deployed to environment 'test'. For example

```sh
adt create apiproxy -n api-httpbin-proxy --proxy-dir ../api-httpbin-proxy.zip -d -e test
```

## UPDATE API PROXY

Updates an existing revison of an API proxy by uploading an API proxy configuration bundle as a zip file or apiproxy directory from your local machine.
If the API proxy revision is deployed, the API undeploys the revision, updates it, and then redeploys it. If the API proxy revision is not deployed, the API updates the revision but does not deploy it.

CAUTION: The API proxy is immediately updated in all environments where it is deployed.
### USAGE

```sh
adt update apiproxy --help
Operation on API Proxy.
Usage: adt update apiproxy [-hV] -n=<name> -p=<input> -r=<revision>
                           [-x=<proxyHost>]
  -h, --help                Show this help message and exit.
  -n, --name=<name>         The name of API proxy.
  -p, --proxy-dir=<input>   Location of apiproxy directory/zip.
  -r, --revision=<revision> The revision to update.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.

  ```
#### Update using a zipped bundled
```sh
adt update apiproxy -n api-httpbin-proxy-v1 -p ../api-httpbin-proxy-v1.zip -r 2
```

#### Update using apiproxy directory.

```sh
adt update apiproxy -n api-httpbin-proxy-v1 -p ../api-httpbin-proxy-v1 -r 2
```

## QUERY API PROXY

### USAGE

```sh
Operation on API Proxy.
Usage: adt list apiproxy [-hV] [--list-revision] [-n=<name>] [-o=<output>]
                         [-r=<revision>] [-x=<proxyHost>]
  -h, --help                Show this help message and exit.
      --list-revision       List API proxy revision(s).
  -n, --name=<name>         The name of API proxy.
  -o, --output=<output>     The API proxy as zipped output.
  -r, --revision=<revision> The API proxy revision.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
  ```

#### List all api proxies in organization

```sh
adt list apiproxy 
```

#### Query proxy with name

```sh
adt list apiproxy -n api-httpbin-proxy 
```

#### List all revisions of a proxy

```sh
adt list apiproxy -n api-httpbin-proxy --list-revision
```

#### List proxy with revision

```sh
adt list apiproxy -n api-httpbin-proxy -r 1
```

#### Download a revision of a proxy
The below would download a revision of proxy to /tmp location. 

```sh
adt list apiproxy -n api-httpbin-proxy -r 1 -o /tmp
```




## DELETE API PROXY

Deletes an API proxy and all associated endpoints, policies, resources, and revisions. The API proxy must be undeployed before you can delete it. Refer to undeploy API proxy documentation.

### USAGE

```sh
Operation on API Proxy.
Usage: adt delete apiproxy [-hV] -n=<name> [-r=<revision>]
  -h, --help          Show this help message and exit.
  -n, --name=<name>   The name of API proxy.
  -r, --revision=<revision>
                      Location of apiproxy directory.
  -V, --version       Print version information and exit.

  ```
#### Delete API Proxy (all revisions)



#### Delete API Proxy revision





