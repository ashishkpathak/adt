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

## QUERY shared flow

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


