# API PROXY
## CREATE API PROXY
Creates an API Proxy using one of the methods described below. The API proxy created will not be accessible at runtime until it is deployed to an environment.



### USAGE

```sh
adt create apiproxy --help
```

```sh
Operation on API Proxy.
Usage: adt create apiproxy [-dhV] [-b=<bundle>] [-e=<env>] -n=<name>
                           [-p=<input>] [-x=<hostPort>]
  -b, --bundled-zip=<bundle>
                            Location of bundled proxy zip file.
  -d, --deploy              Optionally deploy the proxy.
  -e, --env=<env>           Environment to deploy into.
  -h, --help                Show this help message and exit.
  -n, --api-name=<name>     The name of API proxy.
  -p, --proxy-dir=<input>   Location of apiproxy directory.
  -V, --version             Print version information and exit.
  -x, --http-proxy=<hostPort>
                            Use http proxy (host:port)
```                            
  
#### Import an API Proxy Bundle

Import an API proxy configuration bundle stored as a zip file on your local machine to your organization on Edge by doing the following.


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


## UPDATE API PROXY

Updates an existing revison of an API proxy by uploading an API proxy configuration bundle as a zip file or apiproxy directory from your local machine.
### USAGE

```sh
adt update apiproxy --help
Operation on API Proxy.
Usage: adt update apiproxy [-hV] [-i=<input>] -n=<name>
  -h, --help            Show this help message and exit.
  -i, --input=<input>   Location of apiproxy directory.
  -n, --name=<name>     The name of API proxy.
  -V, --version         Print version information and exit.

  ```
#### Update using a zipped bundled

#### Update using root of apiproxy directory, containing the proxy.



## DELETE API PROXY

Deletes an API proxy and all associated endpoints, policies, resources, and revisions. The API proxy must be undeployed before you can delete it.

### USAGE


