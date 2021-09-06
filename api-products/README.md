## ReadMe
Creates an API Product using one of the methods described below. The API product created will not be accessible at runtime until it is deployed to an environment.


# Usage

```sh
adt create product --help
```

```sh
Operation on API product.
Usage: adt create product [-hV] [-i=<input>] [-n=<name>] [-x=<hostPort>]
  -h, --help          Show this help message and exit.
  -i, --product-config=<input>
                      Location of product config file.
  -n, --name=<name>   The name of product.
  -V, --version       Print version information and exit.
  -x, --http-proxy=<hostPort>
                      Use http proxy (host:port)
```                            
  
## Import an API Product Configuration

Import an API proxy configuration file on your local machine to your organization on Edge by doing the following.


```sh

adt create product -n <api-proxy-name> --product-config <product-config-location>

```

Example

```sh
adt create product -n product-httpbin-v1 --proxy-dir ../apiproduct-httpbin-v1/apiproduct-httpbin-v1.json
```

  The structure of apiproduct-httpbin-v1 as an example is

```sh
├── apiproduct-httpbin-v1
│   └── apiproduct-httpbin-v1.json
```

```json
{
  "apiResources": [
    "/"
  ],
  "approvalType": "auto",
  "attributes": [{
      "name": "access",
      "value": "public"
    },
    {
      "name": "cost",
      "value": "free"
    },
    {
      "name": "working",
      "value": "nothing"
    }
  ],
  "description": "api product httpbin v1 ",
  "displayName": "api product httpbin v1",
  "environments": [
    "test"
  ],
  "name": "product-httpbin-v1",
  "proxies": [
    "api-httpbin-v1"
  ],
  "scopes": []
}
```
