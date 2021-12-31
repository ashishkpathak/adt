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

## Delete Extension

### Usage