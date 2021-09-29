# DEBUG SESSION

## CREATE DEBUG SESSIONS

### Usage

```sh
A.D.T
Operation on debug sessions.
Usage: adt create debug-session [-hV] -a=<apiName> -e=<envName> -n=<sessionName> -r=<revision> [--time-out=<timeout>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --api-proxy=<apiName>  The API Proxy for which debug session created.
  -e, --env=<envName>        The environment where debug session created.
  -h, --help                 Show this help message and exit.
  -n, --session-name=<sessionName>
                             The session name.
  -r, --revision=<revision>  The API proxy revision for which debug session created.
      --time-out=<timeout>   Time in seconds after which the particular session should be discarded. Default 600 seconds.
  -V, --version              Print version information and exit.
  -x, --proxy=<proxyHost>    Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1
Copyright (2021)
```
Creeate a debug session on api-proxy () with revision (r) on environment (e) with name (n).

```sh
adt create debug-session -a api-httpbin-proxy-v1 -r 4 -e dev -n my-debug-sessions 
```


## LIST DEBUG SESSIONS

Lists debug sessions that were created either by using the Create debug session API or the Trace tool in the Edge UI.

### USAGE
```sh
A.D.T
Operation on Environments.
Usage: adt list debug-session [-hV] -a=<apiName> -e=<envName> [-n=<sessionName>] -r=<revision> [-t=<transactionId>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --api-proxy=<apiName> The API Proxy for which debug session created.
  -e, --env=<envName>       The environment where debug session created.
  -h, --help                Show this help message and exit.
  -n, --session-name=<sessionName>
                            The session name.
  -r, --revision=<revision> The API proxy revision for which debug session created.
  -t, --transaction-id=<transactionId>
                            The session transaction id.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1
Copyright (2021)
```

List debug session for api-proxy () with revision () on environment (env).

```sh
adt list debug-session -a api-httpbin-proxy-v1 -e dev -r 4
```

### LIST DEBUG SESSION DATA

Gets transaction IDs for a debug session that was created either by using the Create debug session API or the Trace tool in the Edge UI.
Each item in the returned list is the unique ID for a debug session transaction associated with a single request to the API proxy specified.
Use the Get debug session transaction data API to retrieve the raw debug data for the transaction.

```sh
adt list debug-session -a api-httpbin-proxy-v1 -e dev -r 4 -n my-debug-sessions
```


### LIST DEBUG SESSION TRANSACTION DATA

Gets debug session transaction data. To get a list of transaction IDs, see Get debug session transaction IDs.
The debug data returned by this APl is the same debug data that populates the Trace tool in the Edge management UI. For more information on the Trace tool, see Using the Trace tool.

```sh
adt list debug-session -a api-httpbin-proxy-v1 -e dev -r 4 -n my-debug-sessions -t traceId-123456789
```


## DELETE DEBUG SESSION

Deletes a debug session.

```sh
A.D.T
Remove various modules.
Usage: adt delete [-hV] [COMMAND]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -h, --help      Show this help message and exit.
  -V, --version   Print version information and exit.
Commands:
  apiproxy       Operation on API Proxy.
  shared-flow    Operation on Shared Flows.
  developer      Operation on App.
  product        Operation on product.
  app            Operation on App.
  token          Operation on API Proxy.
  target-server  Operation on target server
  user           Operation on user.
  kvm            Operation on KVM.
Exit Code:
Version 0.0.1
Copyright (2021)
```

```sh
adt delete debug-session -a api-httpbin-proxy-v1 -e dev -r 4 -n my-debug-sessions
```

