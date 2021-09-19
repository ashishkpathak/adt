# ALERT
Creates an alerts using the methods described below. .


You can set up a maximum of 20 alerts per organization. The alert settings apply to all users in the organization; they are not per user. If you change the alert settings, they change for all users in your organization

Edge imposes a quota on this API of 60 calls per minute per organization. This quota is calculated by multiplying 20 (number of allowed alerts) * 3 = 60 calls.

## CREATE ALERT

### USAGE

```sh
adt create alert --help
```

```sh

```                            
  
#### Import an Alert Configuration

Import an alert configuration file on your local machine to your organization on Edge by doing the following.


```sh
adt create alert -n <api-product-name> --product-config <product-config-location>
```

Example

```sh
adt create product -n "API 5xx error rate" --alert-config ../alert-httpbin-v1/alert-httpbin-v1.json
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


### USAGE

Note: You must include all required values, whether or not you are updating them, as well as any optional values that you are updating.

```sh
adt update alert -n <alert-name> --alert-config <alert-config-location>
```

## DELETE ALERT

Delete an alert.

Edge imposes a quota on this API of 60 calls per minute per organization. This quota is calculated by multiplying 20 (number of allowed alerts) * 3 = 60 calls.


### USAGE

```sh
adt delete alert --alert-id <alert-id>
```
