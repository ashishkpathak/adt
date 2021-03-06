# DEBUG SESSION

## CREATE DEBUG SESSIONS

Creates a debug session.

A debug session records detailed information on messages, flow processing, and policy execution during processing by an API proxy.

The data returned in the debug session is a single XML or JSON representation of all debug data for each message exchange. The debug data is the same as that used to generate the Trace view in the Edge UI.

A debug session captures a maximum of 20 messages or records for a maximum of 10 minutes (by default), whichever comes first.

Debugging involves the following steps:

- Start a debug session by creating a debug session.
- Send a message for that deployed API proxy.
- Retrieve the debug data associated with the debug session. The data can be fetched by issuing a GET call on the session.
- Close the debug session. (Closing the debug session discards all the associated data).

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


```
Create a debug session on api-proxy () with revision (r) on environment (e) with name (n).

```sh
adt create debug-session -a api-httpbin-proxy-v1 -r 4 -e dev -n my-debug-sessions 
```


## LIST DEBUG SESSIONS

Lists debug sessions that were created either by using the Create debug session API or the Trace tool in the Edge UI.

### USAGE
```sh
A.D.T
Operation on debug session.
Usage: adt list debug-session [-hV] -a=<apiName> -e=<envName> [-n=<sessionName>] [-o=<output>] -r=<revision> [-t=<transactionId>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --api-proxy=<apiName> The API Proxy for which debug session created.
  -e, --env=<envName>       The environment where debug session created.
  -h, --help                Show this help message and exit.
  -n, --session-name=<sessionName>
                            The session name.
  -o, --output=<output>     Output the debug session to file.
  -r, --revision=<revision> The API proxy revision for which debug session created.
  -t, --transaction-id=<transactionId>
                            The session transaction id.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:


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
Operation on debug session.
Usage: adt delete debug-session [-hV] -a=<apiName> -e=<envName> -n=<sessionName> -r=<revision> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --api-proxy=<apiName> The API Proxy for which debug session created.
  -e, --env=<envName>       The environment where debug session created.
  -h, --help                Show this help message and exit.
  -n, --session-name=<sessionName>
                            The session name to delete.
  -r, --revision=<revision> The API proxy revision for which debug session created.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:

```

```sh
adt delete debug-session -a api-httpbin-proxy-v1 -e dev -r 4 -n my-debug-sessions
```

