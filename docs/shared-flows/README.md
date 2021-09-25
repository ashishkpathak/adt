# SHARED FLOW
## CREATE SHARED FLOW
Creates an shared flow using one of the methods described below. The shared flow created will not be accessible at runtime until it is deployed to an environment.



### USAGE

```sh
adt create shared-flow --help
```

```sh
Operation on Shared Flows.
Usage: adt create shared-flow [-dhV] [-e=<env>] -n=<name> [-p=<input>]
                              [-x=<hostPort>]
  -d, --deploy      Optionally deploy the shared flow.
  -e, --env=<env>   Environment to deploy into.
  -h, --help        Show this help message and exit.
  -n, --shared-flow-name=<name>
                    The name of shared flow.
  -p, --shared-flow-dir=<input>
                    Location of shared flow directory.
  -V, --version     Print version information and exit.
  -x, --http-proxy=<hostPort>
                    Use http proxy (host:port)
```                            
  
Note: Shared flows using the create command, get created by not deployed. To create and deploy shared-flows, refer to below documentation.

#### Import an shared flow directory.

Import an shared flow configuration stored on local machine as following directory structure.


```sh
adt create shared-flow -n <api-proxy-name> -p <proxy-location>
```

Example

```sh
adt create shared-flow -n sf-quota -p ../sf-quota/
```

The structure of sf-quota as an example is

```sh
sf-quota
└── sharedflowbundle
    ├── policies
    │   ├── QP_QuotaDefaults.xml
    │   └── RF_QuotaViolation.xml
    ├── sf-quota-policy.xml
    └── sharedflows
        └── default.xml
```

#### Import a zipped bundle

Import an shared flow bundle stored as a zip file on your local machine to your organization on Edge by doing the following.

```sh
adt create shared-flow -n sf-quota -p ../sf-quota.zip
```

NOTE: ADT can take **relative** and **absolute** paths.

Optionally the created proxy can be deployed to environment 'test'. For example

```sh
adt create apiproxy -n sf-quota -p ../sf-quota.zip -d -e test
```

## UPDATE shared flow

Updates an existing revison of an shared flow by uploading an shared flow configuration bundle as a zip file or sharedflowbundle directory from your local machine.
If the shared flow revision is deployed, the API undeploys the revision, updates it, and then redeploys it. If the shared flow revision is not deployed, the API updates the revision but does not deploy it.

CAUTION: The shared flow is immediately updated in all environments where it is deployed.
### USAGE

```sh
adt update shared-flow --help
Operation on shared flow.
Usage: adt update shared-flow [-hV] -n=<name> -p=<input> -r=<revision>
                           [-x=<proxyHost>]
  -h, --help                Show this help message and exit.
  -n, --name=<name>         The name of shared flow.
  -p, --proxy-dir=<input>   Location of apiproxy directory/zip.
  -r, --revision=<revision> The revision to update.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.

  ```
#### Update using a zipped bundled
```sh
adt update shared-flow -n sf-quota-v1 -p ../sf-quota-v1.zip -r 2
```

Sample response:

```json
{
  "type" : "Application",
  "targets" : [ "default" ],
  "basepaths" : [ "/api/httpbin/v1" ],
  "configurationVersion" : {
    "majorVersion" : 4,
    "minorVersion" : 0
  },
  "contextInfo" : "Revision 1 of application -NA-, in organization -NA-",
  "createdAt" : 1631169016214,
  "createdBy" : "deploytool@enterprise.com",
  "description" : "Demo httpbin proxy.",
  "displayName" : "sf-quota-v1",
  "entityMetaDataAsProperties" : {
    "lastModifiedBy" : "deploytool@enterprise.com",
    "createdBy" : "deploytool@enterprise.com",
    "lastModifiedAt" : 1631504642400,
    "subType" : "null",
    "createdAt" : 1631169016214,
    "bundle_type" : "zip"
  },
  "lastModifiedAt" : 1631504642400,
  "lastModifiedBy" : "deploytool@enterprise.com",
  "manifestVersion" : "SHA-512:69d3bd8cec45692725320422fd8343edf7497f3e7f843a3863cbfaa8f885dc1bf7d25aa3ae310475a7fa43b3eefee5d0843e93029d1a2b8d9a3faf1f90b8c0e6",
  "policies" : [ ],
  "proxies" : [ "default" ],
  "resources" : [ ],
  "revision" : "1",
  "sharedFlows" : [ ],
  "spec" : "",
  "proxyEndpoints" : [ "default" ],
  "targetServers" : [ ],
  "targetEndpoints" : [ "default" ],
  "name" : "sf-quota-v1"
}
```

#### Update using shared-flow directory.

```sh
adt update shared-flow -n sf-quota-v1 -p ../sf-quota-v1 -r 2
```

### Update a shared flow. Attach to flow hook.

Attaches a shared flow to the specified flow hook. Valid values for flow hook include:

    PreProxyFlowHook
    PreTargetFlowHook
    PostTargetFlowHook
    PostProxyFlowHook

```sh
adt update shared-flow -f PreProxyFlowHook -p ../fh-quota-config-location
```
Example of fh-quota-config.json 

```json
{
  "FlowHook": {
    "SharedFlow": "mySharedFlow"
  }
}
```

Successful response: 
```json

{
  "continueOnError": true,
  "sharedFlow": "mySharedFlow",
  "state": "deployed"
}

```
## LIST shared flow

### USAGE

```sh
Operation on Shared Flows.
Usage: adt list shared-flow [-hV] [--list-revision] [-i=<input>] [-n=<name>]
                            [-o=<output>] [-r=<revision>]
  -h, --help              Show this help message and exit.
  -i, --input=<input>     Location of shared flow config file.
      --list-revision     List shared flow revision(s).
  -n, --name=<name>       The name of shared flow.
  -o, --output=<output>   The shared flow as zipped output.
  -r, --revision=<revision>
                          Shared flow revision.
  -V, --version           Print version information and exit.
  ```

#### List all shared flows in organization

```sh
adt list shared-flow 
```

#### Query proxy with name

```sh
adt list shared-flow -n sf-quota 
```

#### List all revisions of a proxy

```sh
adt list shared-flow -n sf-quota --list-revision
```

<!-- #### List proxy with revision

```sh
adt list apiproxy -n sf-quota -r 1
``` -->

#### Download a revision of a shared-flow
The below would download a revision of shared-flow to /tmp location. 

```sh
adt list apiproxy -n sf-quota -r 1 -o /tmp
```
## LIST shared flow attached to flow hooks

```sh
adt list shared-flow --flow-hook <FlowHook>
```
Can provide any of the following flow hooks
  PreProxyFlowHook
  PreTargetFlowHook
  PostTargetFlowHook
  PostProxyFlowHook

```sh
adt list shared-flow -f PreProxyFlowHook -e dev
```





## DELETE shared flow

Deletes an shared flow and all associated endpoints, policies, resources, and revisions. The shared flow must be undeployed before you can delete it. Refer to undeploy shared flow documentation.

### USAGE

```sh
Operation on shared flow.
Usage: adt delete shared-flow [-hV] -n=<name> [-r=<revision>]
  -h, --help          Show this help message and exit.
  -n, --name=<name>   The name of shared flow.
  -r, --revision=<revision>
                      Location of apiproxy directory.
  -V, --version       Print version information and exit.

  ```
#### Delete shared flow (all revisions)

```sh
adt delete shared-flow --name sf-quota
```

#### Delete shared flow revision

```sh
adt delete shared-flow --name sf-quota --revision 2 
```

#### Detach a shared flow from flow hook.

Detaches a shared flow from the specified flow hook. Valid values for flow hook include:

    PreProxyFlowHook
    PreTargetFlowHook
    PostTargetFlowHook
    PostProxyFlowHook If no shared flow is attached, this will not return an error. Only one shared flow at a time can be attached to a flow hook.

```sh
adt delete shared-flow -f <flow-hook>
```
Sample response

```json
{
  "continueOnError": true,
  "sharedFlow": "mySharedFlow",
  "state": "undeployed"
}
```

## DEPLOY shared flow

### Usage
```sh
Usage: adt deploy shared-flow [-hV] [--delay=<delay>] -e=<env> -n=<name> [--override=<override>] -r=<revision> [-x=<hostPort>]

      --delay=<delay>   Time interval, in seconds, to wait before undeploying the currently deployed API proxy revision. Use this setting in conjunction with override parameter to minimize
                          the impact of deployment on in-flight transactions and the occurrence of 502 Bad Gateway or 504 Gateway.
  -e, --env=<env>       Environment to deploy into.
  -h, --help            Show this help message and exit.
  -n, --shared-flow-name=<name>
                        The name of shared flow.
      --override=<override>
                        Flag that specifies whether to force the deployment of the new revision over the currently deployed revision. Set this parameter to true to provide seamless
                          deployment. In this case, the existing revision remains deployed until the new revision is fully deployed. Use in conjunction with the delay parameter to control
                          undeployment and minimize the impact on in-flight transaction. If set to false, you must undeploy the currently deployed revision before deploying the new revision.
  -r, --revision=<revision>
                        Revision of shared flow to deploy.
  -V, --version         Print version information and exit.
  -x, --http-proxy=<hostPort>
                        Use http proxy (host:port)
```

```sh
adt deploy shared-flow -n <shared-flow-name> -r <revision> -e <environment>
```

## UNDEPLOY shared flow

### Usage

```sh
Usage: adt undeploy shared-flow [-hV] -e=<env> -n=<name> -r=<revision> [-x=<hostPort>]

  -e, --env=<env>     Environment details.
  -h, --help          Show this help message and exit.
  -n, --name=<name>   The name of proxy or shared flow.
  -r, --revision=<revision>
                      The revision details.
  -V, --version       Print version information and exit.
  -x, --http-proxy=<hostPort>
                      Use http proxy (host:port)

```

```sh
adt undeploy shared-flow -n <shared-flow> -e <env> -r <revision>
```