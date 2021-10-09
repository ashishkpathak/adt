# ENVIRONMENT

## CREATE ENVIIRONMENT

Creates an environment in an existing organization.

Notes:

    Apigee Edge for Private Cloud only. If you are using Apigee Edge for Public Cloud, contact Apigee Support for assistance.
    This API cannot be executed using the Try this API panel.

After you create the environment, you must:

    Associate the environment with one or more Message processors. See Associate an environment with a Message Processor.
    Enable analytics on the environment. See Enable analytics for an environment.

Edge provides scripts and other tools that you can use as an alternative to making API calls directly. For example, see Creating an organization, environment, and virtual host.

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

