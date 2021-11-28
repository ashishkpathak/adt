# Cached Logs

Access cached log for an API.

## Usage

```sh
A.D.T
Operation on Cached Logs.
Usage: adt list cached-log [-hV] -a=<apiProxy> [-c=<category>] -e=<environment> [-s=<state>] [-tz=<tz>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -a, --api-proxy=<apiProxy>
                            The API proxy.
  -c, --category=<category> The category : nodejs, hostedtarget-build, hostedtarget-buildtme.
  -e, --env=<environment>   The environment to create cache in.
  -h, --help                Show this help message and exit.
  -s, --state=<state>       The state to continue from.
      -tz=<tz>              The timezone. EST or PST.
  -V, --version             Print version information and exit.
  -x, --http-proxy=<proxyHost>
                            Host:Port of the proxy server to use.
Version 1.0.1

```

## List cached logs categories.
Lists the names of the available cached log categories for the specified API.

Categories include:

- nodejs
- hostedtarget-build
- hostedtarget-runtime

```sh
adt list cached-log -a <api-name> -e <environment>
```


## List cached logs for a specific category.

Gets the most recent log records for the specified API and category.

Supported categories include:

- nodejs - Logs for Node.js proxy applications.
- hostedtarget-build - Build logs for Hosted Targets applications.Shows you output related to deploying and building the Node.js app.
- hostedtarget-runtime - Runtime logs for for Hosted Targets applications. Shows output related to the running app. Runtime logs are scoped to the environment and return logs for the currently deployed proxy revision.

The exact number of log records returned may change depending on system configuration, but it will typically be 500 for each message processor or 1000 in most configurations. Hosted Target logs are retained for 7 days or 50 GBs per month, whichever comes first.

The response format is as follows:

```sh
[TIMESTAMP CATEGORY SERVER] Record...
```
Where:

-   TIMESTAMP: Time at which the log record was generated.
-   CATEGORY: Log category (nodejs, hostedtarget-build, or hostedtarget-runtime) and whether the log went to stdout or stderr.
-   SERVER:
        For Node.js, uniquely identifies the server within Apigee Edge where the log was generated. For example: [2014-10-09T00:58:17.619Z nodejs/stdout svr.701]Hello, World!
        For Hosted Targets, SERVER is always reported as: svr.0


Example Hosted Targets runtime log output:

```text
[2018-01-19T18:09:18.118Z hostedtarget-runtime/stdout svr.0] GET /
[2018-01-19T18:09:21.286Z hostedtarget-runtime/stdout svr.0] The time is  2018-01-19T18:06:18.182Z

```

Example Hosted Targets build log output:

```text
[2018-01-19T18:03:53.000Z hostedtarget-build/stdout svr.0] Starting Step #0
[2018-01-19T18:03:53.000Z hostedtarget-build/stdout svr.0] Step #0: Pulling image: gcr.io/turbo-validators/nodevalidation:0.0.1
[2018-01-19T18:03:53.000Z hostedtarget-build/stdout svr.0] Step #0: 0.0.1: Pulling from turbo-validators/nodevalidation

```


```sh
adt list cached-log -a <api-name> -e <environment> -c <category>
```