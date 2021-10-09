# DEPLOYMENTS

## DEPLOY AN API PROXY/ SHARED FLOW.

### Usage Deploy

```sh
A.D.T
Deploy apiproxy and shared-flows.
Usage: adt deploy [-hV] [COMMAND]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -h, --help      Show this help message and exit.
  -V, --version   Print version information and exit.
Commands:
  apiproxy     Deploy an API Proxy.
  shared-flow  Operation on Shared Flows.
Exit Code:
Version 0.0.1

```


### Usage Deploy API Proxy

Usage

```sh
A.D.T
Deploy an API Proxy.
Usage: adt deploy apiproxy [-hV] [--delay=<delay>] -e=<env> -n=<name> [--override=<override>] -r=<revision> [-x=<hostPort>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
      --delay=<delay>     Time interval, in seconds, to wait before undeploying the currently deployed API proxy revision. Use this setting in conjunction with override parameter to
                            minimize the impact of deployment on in-flight transactions and the occurrence of 502 Bad Gateway or 504 Gateway.
  -e, --env=<env>         Environment to deploy into.
  -h, --help              Show this help message and exit.
  -n, --api-name=<name>   The name of API proxy.
      --override=<override>
                          Flag that specifies whether to force the deployment of the new revision over the currently deployed revision. Set this parameter to true to provide seamless
                            deployment. In this case, the existing revision remains deployed until the new revision is fully deployed. Use in conjunction with the delay parameter to control
                            undeployment and minimize the impact on in-flight transaction. If set to false, you must undeploy the currently deployed revision before deploying the new
                            revision.
  -r, --revision=<revision>
                          Revision of API to deploy.
  -V, --version           Print version information and exit.
  -x, --http-proxy=<hostPort>
                          Use http proxy (host:port)
Exit Code:
Version 0.0.1
```

Deploy API proxy 

```sh
adt deploy apiproxy -n api-httpbin-proxy-v1 -r 1 -e dev -x proxyhost:3129
```

### Usage Undeploy API Proxy

```sh
A.D.T
Undeploy an API Proxy.
Usage: adt undeploy apiproxy [-hV] -e=<env> -n=<name> -r=<revision> [-x=<hostPort>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -e, --env=<env>     Environment to undeploy from.
  -h, --help          Show this help message and exit.
  -n, --name=<name>   The name of API Proxy.
  -r, --revision=<revision>
                      The revision number to undeploy.
  -V, --version       Print version information and exit.
  -x, --http-proxy=<hostPort>
                      Use http proxy (host:port)
Exit Code:
Version 0.0.1
```


Undeploy apiproxy api-httpbin-proxy-v1 with revision 2 in environment dev.

```sh
adt undeploy apiproxy -n api-httpbin-proxy-v1 -r 2 -e dev
```


## LIST DEPLOYMENTS

Lists all API proxies that are deployed for environments/revisions in an organization.

### Usage
```sh
A.D.T
Operation on Deployments.
Usage: adt list deployment [-hV] [--api-config] [--server-status] [-e=<env>] [-n=<name>] [-r=<revision>] [-t=<type>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
      --api-config          Include API config
                              Default: false
  -e, --env=<env>           Environment to deploy
  -h, --help                Show this help message and exit.
  -n, --name=<name>         The api-proxy or shared-flow name.
  -r, --revision=<revision> The revision to deploy
      --server-status       Include server status
                              Default: false
  -t, --type=<type>         Deployment type: api-proxy or shared-flow.
                              Default: api-proxy
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1
```

Lists all API proxies that are deployed for all environments in an organization.

```sh
adt list deployment

```
Lists all API proxies that are deployed to the specified environment. The server information is used by Apigee support to identify servers that support the API proxy deployment.

```sh
adt list deployment -e test
```

List deployments of an API proxy/Shared Flows.  Gets details for all deployments of the API proxy across all environments (test, prod, and so on)

```sh
adt list deployment -n api-httpbin-proxy-v1
```

List deployment of an API Proxy and include server status information. To include api-config pass --api-config option.

```sh
adt list deployment -n api-httpbin-proxy-v1 --server-status
```
List deployment of shared flow.  Use option --type/-t to distinguish between apiproxy and shared-flows.

```sh
adt list deployment -n TokenSecurity -t shared-flow
```

Sample response

```json
{
  "organization" : "myorg-nonprod",
  "environment" : [ {
    "name" : "dev",
    "revision" : [ {
      "configuration" : null,
      "name" : "1",
      "server" : [ ],
      "state" : "deployed"
    } ],
    "state" : null,
    "aPIProxy" : null
  } ],
  "name" : "TokenSecurity"
}
```

