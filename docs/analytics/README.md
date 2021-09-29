# ANALYTICS

Creates an analytics using the methods described below. 

## CREATE ANALYTICS

Enables analytics for an environment
**Apigee Edge for Private Cloud only.**

### USAGE

```sh
adt create analytics --enable
```
After you create an environment, you can enable analytics for the environment. If you wish to enable analytics for one environment, you must enable analytics for all environments in the organization.

You must pass the entries for Analtyics onboarding in a file named sample.json. For example:    
```sh
{
  "properties" : {
    "samplingAlgo" : "reservoir_sampler",
    "samplingTables" : "10=ten;1=one;",
    "aggregationinterval" : "300000",
    "samplingInterval" : "300000",
    "useSampling" : "100",
    "samplingThreshold" : "100000"
  },
  "servers" : {
    "postgres-server" : [ "1acff3a5-8a6a-4097-8d26-d0886853239c", "f93367f7-edc8-4d55-92c1-2fba61ccc4ab" ],
    "qpid-server" : [ "d3c5acf0-f88a-478e-948d-6f3094f12e3b", "74f67bf2-86b2-44b7-a3d9-41ff117475dd"]
  }
}
```
  
#### Create analytics export job request.

Creates an analytics data export job.

The API returns the data export job ID that you use to track the status of the job. You must be in the role of organization administrator to call this API.


Export API quotas

To prevent overuse of expensive data export API calls, Edge enforces a quota on calls to this API:

    For organizations and environments that do not have monetization enabled, the quota is 70 calls per month per organization/environment. For example, if you have two environments in your organization, prod and test, you can make 70 API calls per month for each environment.


```sh
adt create analytics -n <analytics-name> --analytics-config <analytics-config-location>
```

Example


```json
{
  "datastoreName": "My Cloud Storage data repository",
  "dateRange": {
    "start": "2018-06-08",
    "end": "2018-06-09"
  },
  "description": "Export raw results to Cloud Storage for last 24 hours",
  "name": "Export raw results to Cloud Storage",
  "outputFormat": "json"
}
```
#### Create queries

Creates an asynchronous analytics query.

You must be an organization administrator to invoke this operation. You can make up to seven calls per hour. If you exceed the call quota, this API returns an HTTP 429 response.

### USAGE

```sh
adt create analytics --query --query-config <config-location> --env <environment>
```

```json
{
  "metrics": [
    {
      "name": "message_count",
      "function": "sum",
      "alias": "sum_txn"
    }
  ],
  "dimensions": [
    "apiproxy"
  ],
  "timeRange": "last24hours",
  "limit": 14400,
  "filter": "(message_count ge 0)"
}
```

## LIST ANALYTICS

Gets the status of an analytics data export job. Create an export job using the Create an analytics data export job API.

The state property specifies the status of the job and can have one of the following values: enqueued, running, completed, failed



### USAGE

Note: You must include all required values, whether or not you are updating them, as well as any optional values that you are updating.

```sh
adt list analytics -e <environment> --export-id <export-id>
```

Lists the asynchronous analytics queries for an environment.

```sh
adt list analytics --query --query-id <id>
```

Gets the status of an asynchronous analytics query. Obtain the queryId when you created the query by using the Create an asynchronous analytics query API.
In the response, the value of the state property contains the query status as either running or completed.

Gets the results of an asynchronous analytics query. The status value must be set to completed. If the request succeeds, and there is a non-zero result set, the result is downloaded to the client as a zipped JSON (newline-delimited) file. The name of the downloaded file will be: OfflineQueryResult-<query-id>.zip
  
```sh
adt list analytics --query --query-id <id> --output <output file>
```
 
