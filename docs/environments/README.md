# ENVIRONMENT

## CREATE ENVIIRONMENT

### Usage

```sh
ToDo
```
Creates an environment in an existing organization.

```sh
adt create env -i ../env-config.json
```


## LIST ENVIRONMENT

Lists all environments in an organization. By default, an Apigee organization contains two environments: test and prod

### USAGE
```sh
A.D.T
Operation on Environments.
Usage: adt list env [-hsV] [-n=<envName>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -h, --help                Show this help message and exit.
  -n, --name=<envName>      The name of environment.
  -s, --list-servers        List message processors.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:


```

### LIST ENVIRONMENT

Gets environment details, including:

    UNIX times at which the environment was created and last modified
    Email address of the Apigee user who created and last modified the environment
    List of property names and values that are reserved for use by Apigee


```sh
adt list env -n test
```

Sample response 

```json
{
  "createdBy" : "nXXXX@google.com",
  "lastModifiedAt" : 1553269762580,
  "lastModifiedBy" : "nXXXXX@google.com",
  "name" : "dev",
  "properties" : {
    "property" : [ {
      "name" : "offlineQueryEnabled",
      "value" : "true"
    }, {
      "name" : "factquery_spark_enabled",
      "value" : "true"
    }, {
      "name" : "uapEnabled",
      "value" : "true"
    } ]
  }
}
```


### LIST ENVIRONMENT

Lists the UUIDs of the Message Processors associated with the environment.

```sh
adt list env -n test --list-servers
```


## DELETE ENVIRONMENT

Deletes an environment.

```sh
TODO
```

```sh
adt delete env -n test
```

