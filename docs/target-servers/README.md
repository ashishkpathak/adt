# TARGET SERVER
## CREATE TARGET SERVER

Creates a TargetServer in the specified environment.

TargetServers are used to decouple TargetEndpoint HTTPTargetConnections from concrete URLs for backend services. An HTTPConnection can be configured to use a LoadBalancer that lists one or more TargetSevers. Using TargetServers, you can create an HTTPTargetConnection that calls a different backend server based on the environment where the API proxy is deployed. 

### USAGE

```sh
Operation on Target Server.
Usage: adt create target-server [-hV] -e=<env> -n=<name> -p=<input> [-x=<hostPort>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -e, --env=<env>   Environment to create target server into.
  -h, --help        Show this help message and exit.
  -n, --target-server-name=<name>
                    The target server name.
  -p, --target-server-config=<input>
                    Location of target server config.
  -V, --version     Print version information and exit.
  -x, --http-proxy=<hostPort>
                    Use http proxy (host:port)
```

```sh
adt create target-server -e <env> -p <target-server-config>
```

Target server config 

```json
{
  "host" : "my-host.com",
  "name" : "my-host-ts",
  "port" : 443,
  "enabled" : false,
  "sSLInfo" : {
    "ciphers" : [ ],
    "keyAlias" : "alias-key",
    "keyStore" : "ref://alias-ref-01",
    "protocols" : [ ],
    "ignoreValidationErrors" : false,
    "trustStore" : ""
  }
}

```

## LIST TARGET SERVER

List TargetServers in an environment.
### USAGE

```sh
Operation on target server.
Usage: adt list target-server [-hV] -e=<env> [-n=<name>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -e, --env=<env>           Target server scoped to environment.
  -h, --help                Show this help message and exit.
  -n, --name=<name>         The name of target server.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
  ```

  List all TargetServers in an environment.

```sh
adt list target-server -e <env>
```

Gets TargetServer details.

```sh
adt list target-server -e <env> -n <name>
```


## UPDATE TARGET SERVER

Modifies an existing TargetServer. (You can also modify TargetServers in the Edge UI, as described in Load balancing across backend servers.)

For example, use this method to toggles a TargetServer configuration from enabled to disabled. This is useful when TargetServers are used in load balancing configurations, and one or more TargetServers need to taken out of rotation periodically. You could also use this to modify the hostname of an enabled TargetServer.

### USAGE

```sh
Operation on target server.
Usage: adt update target-server [-hV] [-i=<input>] -n=<name> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -h, --help                Show this help message and exit.
  -i, --target-server-config=<input>
                            Location of target server config.
  -n, --name=<name>         The name of target server.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
```

```sh
adt update target-server -e <env> -i <target-server-config> -n <target-server-name>
```
## DELETE TARGET SERVER

Deletes a TargetServer configuration from an environment.

Note: The deletion of a TargetServer can fail if it is referenced by a currently deployed API proxy. Before deleting a TargetServer, check to make sure that it's not referenced by any API proxies that are currently deployed.

### USAGE

```sh
Operation on target server
Usage: adt delete target-server [-hV] -e=<env> -n=<name> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -e, --env=<env>           The environment.
  -h, --help                Show this help message and exit.
  -n, --target-server-name=<name>
                            The target server name, to delete.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
```


```sh
adt delete target-server -n <target-server-name> -e <env>
```
