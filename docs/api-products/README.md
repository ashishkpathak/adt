# API PRODUCT
Creates an API Product using one of the methods described below. The API product created will not be accessible at runtime until it is deployed to an environment.


## CREATE PRODUCT

### USAGE

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
  
#### Import an API Product Configuration

Import an API proxy configuration file on your local machine to your organization on Edge by doing the following.


```sh
adt create product -n <api-product-name> --product-config <product-config-location>
```

Example

```sh
adt create product -n product-httpbin-v1 --product-config ../apiproduct-httpbin-v1/apiproduct-httpbin-v1.json
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
      "name": "scope",
      "value": "read write"
    },
    {
      "name": "quota",
      "value": "10tps"
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

**Warning:**

    If you don't specify an API proxy in the request body, any app associated with the API product can make calls to any API in your entire organization.
    If you don't specify an environment in the request body, the API product allows access to all environments.


## UPDATE PRODUCT

Updates an existing API product.


The API product name required in the request is the internal name of the product, not the display name. While they may be the same, it depends on whether the API product was created via UI or API. View the list of API products to verify the internal name.

### USAGE

Note: You must include all required values, whether or not you are updating them, as well as any optional values that you are updating.

```sh
adt update product -n <api-product-name> --product-config <product-config-location>
```

Example

```sh
adt update product -n product-httpbin-v1 --product-config ../apiproduct-httpbin-v1/apiproduct-httpbin-v1.json
```

## LIST PRODUCT

### USAGE

```sh
Operation on product.
Usage: adt list product [-AehV] [-a=<attribute>] [-c=<count>] [-n=<name>] [-s=<startKey>] [-v=<attributeValue>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --attribute-name=<attribute>
                            The product attribute name.
  -A, --list-attributes     List the attributes.
  -c, --count=<count>       The number of products to return in API call.
  -e, --expand              To view expanded form of products
  -h, --help                Show this help message and exit.
  -n, --name=<name>         The name of API Product.
  -s, --start=<startKey>    The name of API product to start displaying from.
  -v, --attribute-value=<attributeValue>
                            The product attribute value
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
```

List all products in an organization. This returns the name of the products, to see them in expanded form use the -e option.

```sh 
adt product list
```

Optionally list products with an attribute or attribute value or both

```sh
adt product list -a <attribute-name> -v <attribute-value> -c <number of products to return>
```

List a product with a name.

```sh
adt product list -n <product-name>
```
