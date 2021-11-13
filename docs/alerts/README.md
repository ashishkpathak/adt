# ALERT
Creates an alerts using the methods described below. .


You can set up a maximum of 20 alerts per organization. The alert settings apply to all users in the organization; they are not per user. If you change the alert settings, they change for all users in your organization

Edge imposes a quota on this API of 60 calls per minute per organization. This quota is calculated by multiplying 20 (number of allowed alerts) * 3 = 60 calls.

## LIST ALERT

Lists alerts for an organization.
Note: Edge imposes a quota on this API of 60 calls per minute per organization. This quota is calculated by multiplying 20 (number of allowed alerts) * 3 = 60 calls.

Use Get Alerts to get the UUIDs of all alerts for an organization.

### USAGE
```sh
adt list alert
```

Gets an alert definition.

Note: Edge imposes a quota on this API of 60 calls per minute per organization. This quota is calculated by multiplying 20 (number of allowed alerts) * 3 = 60 calls.
Use List Alert to get the UUIDs of all alerts for an organization.

More information and examples of this API see <a href ="https://docs.apigee.com/api-monitoring/alerts-notifications-api"> Managing Alerts and Notifications</a>

Get Alert with UUID

```sh
adt list alert --alert-id <alert-uuid>
```

## CREATE ALERT

You can set up a maximum of 20 alerts per organization. The alert settings apply to all users in the organization; they are not per user. If you change the alert settings, they change for all users in your organization.

Note: Edge imposes a quota on this API of 60 calls per minute per organization. This quota is calculated by multiplying 20 (number of allowed alerts) * 3 = 60 calls.

More information and examples of this API see <a href ="https://docs.apigee.com/api-monitoring/alerts-notifications-api"> Managing Alerts and Notifications</a>

### USAGE

```sh
adt create alert --help
```

```sh
A.D.T
Operation on Alerts.
Usage: adt create alert [-hV] -i=<alertConfig> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help      Show this help message and exit.
  -i, --alert-config=<alertConfig>
                  The alert config location.
  -V, --version   Print version information and exit.
  -x, --http-proxy=<proxyHost>
                  Host:Port of the proxy server to use.
Version 1.0.1
```                            
  
#### Import an Alert Configuration

Import an alert configuration file on your local machine to your organization on Edge by doing the following.


```sh
adt create alert --alert-config <alert-config-location>
```

Example

```sh
adt create alert --alert-config ../alert-httpbin-v1/alert-httpbin-v1.json
```

The structure of alert-httpbin-v1 as an example is

```sh
├── alert-httpbin-v1
│   └── alert-httpbin-v1.json
```

```json
{
  "name": "API 5xx error rate",
  "enabled": true,
  "description": "Proxy for UI traffic going to back end services",
  "conditions": [
    {
      "description": "",
      "dimensions": {
        "env": "prod",
        "org": "myorg",
        "proxy": "myproxy",
        "region": "ANY",
        "statusCode": "5xx"
      },
      "metric": "rate",
      "threshold": 0.02,
      "durationSeconds": 600,
      "comparator": ">"
    }
  ],
  "playbook": "Link to playbook",
  "throttleIntervalSeconds": 3600,
  "self": "/alerts/abcd1234",
  "feed": "/o/apigee-internal/events/abcd1234",
  "organization": "myorg",
  "environment": "prod",
  "notifications": [
    {
      "channel": "email",
      "destination": "ahamilton@example.com"
    }
  ],
  "alertType": "runtime",
  "alertSubType": "fixed"
}
```

## UPDATE ALERT

Updates an alert.

Use Get Alerts to get the UUIDs of all alerts for an organization. 

Note:

- You cannot change the organization when updating the alert.
- Edge imposes a quota on this API of 60 calls per minute per organization. This quota is calculated by multiplying 20 (number of allowed alerts) * 3 = 60 calls.


### USAGE



```sh
A.D.T
Operation on Alert.
Usage: adt update alert [-hV] -i=<alertConfig> -n=<alertName> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help               Show this help message and exit.
  -i, --alert-config=<alertConfig>
                           The alert config location.
  -n, --name=<alertName>   The Alert UUID
  -V, --version            Print version information and exit.
  -x, --http-proxy=<proxyHost>
                           Host:Port of the proxy server to use.
Version 1.0.1
```

Note: You must include all required values, whether or not you are updating them, as well as any optional values that you are updating.

```sh
adt update alert -n <alert-uuid> --alert-config <alert-config-location>
```

## DELETE ALERT

Delete an alert.

Edge imposes a quota on this API of 60 calls per minute per organization. This quota is calculated by multiplying 20 (number of allowed alerts) * 3 = 60 calls.


### USAGE

```sh
A.D.T
Operation on Alert.
Usage: adt delete alert [-hV] -n=<alertName> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help               Show this help message and exit.
  -n, --name=<alertName>   The Alert UUID.
  -V, --version            Print version information and exit.
  -x, --http-proxy=<proxyHost>
                           Host:Port of the proxy server to use.
Version 1.0.1
```


```sh
adt delete alert -n <alert-uuid>
```
