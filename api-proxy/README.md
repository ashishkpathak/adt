## API PROXY
Creates an API Proxy using one of the methods described below. The API proxy created will not be accessible at runtime until it is deployed to an environment.


# Usage

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
  
## Import an API Proxy Bundle

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

## Import a zipped bundle
