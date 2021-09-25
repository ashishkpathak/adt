# ORGANIZATION

## Usage



### LIST ORGANIZATION
List all organization. This is a restricted API. Not available for all user/roles.


List organization.

```sh
adt list organization -o <organization-name>
```

Typical response
```json

{
  "createdAt": 1394486446988,
  "createdBy": "noreply_admin@apigee.com",
  "displayName": "myorg",
  "environments": [
    "prod",
    "test",
    "portal"
  ],
  "lastModifiedAt": 1590113466345,
  "lastModifiedBy": "admin@example.com",
  "name": "mmyorg",
  "properties": {
    "property": [
      {
        "name": "features.isCpsEnabled",
        "value": "true"
      },
      {
        "name": "subscriptionType",
        "value": "enterprise"
      }
    ]
  },
  "type": "paid"
}

```

### LIST ORGANIZATION PODS

Lists the pods associated with an organization.

Notes:

    Apigee Edge for Private Cloud only. If you are using Apigee Edge for Public Cloud, contact Apigee Support for assistance.
    This API cannot be executed using the Try this API panel.


```sh
adt list organization -o <organization> --pods
```



## CREATE ORGANIZATION

Creates an organization.

Notes:

    Apigee Edge for Private Cloud only. If you are using Apigee Edge for Public Cloud, contact Apigee Support for assistance.
    This API cannot be executed using the Try this API panel.

After you create the organization, you must:

    Associate the organization with a pod
    Add an organization administrator

Edge provides scripts and other tools that you can use as an alternative to making API calls directly. For example, for Edge 4.16.05 and later, see Creating an organization, environment, and virtual host.

```sh
adt create organization --org-config <org-config-json>
```

org-config-json

```json

{
  "displayName": "myorg",
  "environments": [
    "prod",
    "test",
    "portal"
  ],
  "name": "myorg",
  "properties": {
    "property": [
      {
        "name": "features.isCpsEnabled",
        "value": "true"
      },
      {
        "name": "subscriptionType",
        "value": "enterprise"
      }
    ]
  },
  "type": "paid"
}
```


## UPDATE ORGANIZATION
Updates organization properties.
Notes:

    Apigee Edge for Private Cloud only. If you are using Apigee Edge for Public Cloud, contact Apigee Support for assistance.
    This API cannot be executed using the Try this API panel.

Some Edge functionality is controlled by properties set on an organization. For example, when defining resource paths in API products, you can change the way Edge treats a single forward slash (/) by setting an organization property.

Caution: When updating properties, you must pass all existing properties to the API, even if they are not being changed. If you omit existing properties from the payload in this API call, the properties are removed. To get the current list of properties for the environment, use the Get organization API.

If you attempt to set a property but it doesn't appear in the response payload, then the property must be set by a user in the system administrator role. For Apigee Edg for Public Cloud, contact Apigee Support for assistance with setting properties requiring system administrator role.
Some properties in your organization are reserved and unchangable. For example:

    features.isMonetizationEnabled - Monetization is a paid feature. You can't modify this value.

When you update other organization properties, you must include any existing reserved properties and their current values in order for this update call to succeed.

Available properties are described in the relevant sections of the Edge documentation.

```sh
adt update organization -o <organization-name> --org-config <org-config-location>
```

```json
{
  "properties": {
    "property": [
      {
        "name": "subscriptionType",
        "value": "enterprise"
      }
    ]
  }
}
```
### ASSOCIATE/ DISASSOCIATE POD WITH ORGANIZATION

Associates or disassociates an organization and a pod.

Notes:

    Apigee Edge for Private Cloud only. If you are using Apigee Edge for Public Cloud, contact Apigee Support for assistance.
    This API cannot be executed using the Try this API panel.

By default, the name of the region is dc-1 and the name of the pod is gateway. This names are set by the following properties in the Edge config file when you installed Edge:

MP_POD=gateway
REGION=dc-1    

To associate a pod, pass the following string: region={region_name}&pod={pod_name}

To disassociate a pod, pass the following string: region={region_name}&pod={pod_name}&action=remove

For more information, see the Edge installation instructions.

Disassociate

```sh
adt update organization -o <organization-name> -r <region-name> -p <pod-name> --remove
```

Associate

```sh
adt update organization -o <organization-name> -r <region-name> -p <pod-name> 
```

## DELETE ORGANIZATION

