# Stats

Access metrics collected by Apigee Edge that measure API consumption and performance that are used to build Analytics reports.
## Get Metrics
Get metrics per time interval for an organization and environment. If you are using Edge Microgateway with the analytics plugin enabled (default), API calls to Edge Microgateway are included in the count.

If you have multiple organizations and environments, make this API call for each one and add them to get the total number of calls per time interval for your API program.

To convert the JSON response to a CSV format for use in spreadsheets, use a tool like https://json-csv.com/

For more granular metrics, use the Get metrics organized by dimensions API. For more information on the analytics management API, see Use the metrics APIs.

You can also try the API Traffic Summarizer tool to get and graph traffic data by API proxy over a specific time range.

Metrics

The types of metrics you can retrieve (specifid by the select query parameter) include traffic, message counts, API call latency, response size, and cache hits and counts. See Metrics for more information and for a list of functions (sum, avg, min, max) supported by each metric.

For example, to get the average request size for your APIs, set the select query param as: select=avg(request_size)

To get metrics for the sum of policy errors, transactions per second, and the average request size, set the select query param as: select=sum(policy_error),tps,avg(request_size)

Metrics API quotas

Apigee Edge enforces a quota on the API calls. The quota is based on the backend system that handles the call:

    Postgres: limited to 40 calls per minute.
    BigQuery: limited to 12 calls per minute.

If you exceed the call quota, this API returns an HTTP 429 response.

Determine the backend system that handles the call by examining the response object. Every response object contains a metaData property that lists service that handled the call in the Source property. For example, for Postgres:

{
  ...
  "metaData": {
    "errors": [],
    "notices": [
      "Source:Postgres",
      "Table used: xxxxxx.yyyyy",
      "query served by:111-222-333"
    ]
  }
}

For BigQuery, the Source property is: "Source:Big Query"

### Usage 


#### Get metrics by dimensions.

Gets metrics, groups them by dimensions, and filters the results. If you are using Edge Microgateway with the analytics plugin enabled (default), API calls to Edge Microgateway are included in results.

For examples using this API, see Analytics command reference.

Notes:

    Data delay interval: After API calls are made to API proxies, it may take up to 10 minutes for the data to appear in dashboards, custom reports, and management API calls.
    You can use the _optimized=js query parameter to optimize the JSON in the response so that it is less verbose, as described in this community article. However, the _optimized query parameter has not been fully tested and its performance cannot be guaranteed.

Metrics

The types of metrics you can retrieve (specifid by the select query parameter) include traffic, message counts, API call latency, response size, and cache hits and counts. See Metrics for more information and for a list of functions (sum, avg, min, max) supported by each metric.

For example, to get the average request size for your APIs, set the select query param as: select=avg(request_size)

Note: If you want to use the app_count, developer_count, or user_count metric, you cannot set an aggregation function.

Dimensions:

Dimensions let you view metrics in meaningful groups. For example, instead of looking at total API traffic in your organization, you can see API traffic for each API proxy, for each app, for each developer, and more.

For each dimension, you construct a request by adding the desired dimension in the URL after /stats. For example, to group metrics by API proxies, you'd use: /stats/apiproxy

You can specify multiple dimensions to the API, separated by commas. To group metrics by API proxy and target response code combinations, you'd comma-separate dimensions in the URL: /stats/apiproxy,target_response_code

For a description of all supported dimensions, see Dimensions. You can also include your own custom dimensions, as described in Analyze API message content using custom analytics.

Here's an example that shows how to get the average response time (metric) for all API proxies (dimension) in an environment: /stats/apiproxy?select=avg(total_response_time)

Filters

You can also apply filters to limit the data that's returned. For example, if you're getting message counts grouped by API proxies, you can add a filter that returns only metrics for API proxies that return 4xx or 5xx status codes. Use any available dimensions or metrics to build your filters.

For more information on filters and the operators you can use, see filters.

Metrics API quotas

Apigee Edge enforces a quota on the API calls. The quota is based on the backend system that handles the call:

    Postgres: limited to 40 calls per minute.
    BigQuery: limited to 12 calls per minute.

If you exceed the call quota, this API returns an HTTP 429 response.

Determine the backend system that handles the call by examining the response object. Every response object contains a metaData property that lists service that handled the call in the Source property. For example, for Postgres:

{
  ...
  "metaData": {
    "errors": [],
    "notices": [
      "Source:Postgres",
      "Table used: xxxxxx.yyyyy",
      "query served by:111-222-333"
    ]
  }
}

For BigQuery, the Source property is: "Source:Big Query"

#### Get daily summary reports.
Subscribe to (optin=true) or unsubscribe from (optin=false) daily analytics reports. You must be an organization administrator.

On success, this API returns an HTML-formatted response.

Note: Summary reports are currently available only for environments named prod or production. For more information, see Subscribe to daily analytics emails.


#### Get subscription status for users.

Gets a list of subscribed and unsubscribed users for the daily analytics report.

Notes:

    Apigee Edge for Private Cloud only. If you are using Apigee Edge for Public Cloud, contact Apigee Support for assistance.
    This API cannot be executed using the Try this API panel.

By default, all organization administrators are automatically subscribed to receive daily analytics summary reports through email. A value of "optout": 1 in the response corresponds to the user having opted out, meaning unsubscribed.

