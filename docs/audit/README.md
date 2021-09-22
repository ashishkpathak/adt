# AUDIT
## LIST AUDIT

Lists audit entries for management operations for an organization.

For API proxy revisions, deploy and undeploy actions are recorded as CREATE operations. You can distinguish between them by examining the requestUri element in the output.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against entities in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, this API returns an empty array.

If you omit the timeline, startTime, and endTime parameters, the default is to use timeline=today.

<ToDo>
Help usage

### List all audit entries in organization.

```sh
adt list audit 
```


### List all API product audit entries.

Lists audit entries for management operations for all API products in an organization.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against API products in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, or if the entity does not exist, this API returns an empty array.

If you omit the timeline, startTime, and endTime parameters, the default is to use timeline=today.


```sh
adt list audit --type apiproduct
```

### List API product audit entries.

Lists audit entries for management operations for an API product in an organization.
For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against the specified API product in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, or if the entity does not exist, this API returns an empty array.

If you omit the timeline, startTime, and endTime query parameters, the default is to use timeline=today.

```sh
adt list audit -n <api-product-name> --type apiproduct
```

### List all API proxies audit entries.
Lists audit entries for management operations for all API proxies in an organization.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against API proxies in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, or if the entity does not exist, this API returns an empty array.

```sh
adt list audit --type apiproxy
```

### List API proxies audit entries.

Lists audit entries for management operations for an API proxy in an organization

For API proxy revisions, deploy and undeploy actions are recorded as CREATE operations. You can distinguish between them by examining the requestUri element in the output.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against the specified API proxy in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

```sh
adt list audit -n <api-proxy-name> --type apiproxy
```


### List all Developer audit entries.
Lists audit entries for management operations for all developers in an organization.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against developers in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, or if the entity does not exist, this API returns an empty array


```sh
adt list audit --type developer
```

### List a developer audit entries.

Lists audit entries for management operations for a developer in an organization.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against the specified developer in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, or if the entity does not exist, this API returns an empty array.

```sh
adt list audit -n <developer-email> --type developer
```

## List all Developer App audit entries.
Lists audit entries for management operations for all developer apps in an organization.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against developer apps in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, or if the entity does not exist, this API returns an empty array.


```sh
adt list audit --type developer-app
```

### List a developer app audit entries.

Lists audit entries for management operations for an app in an organization.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against the specified app in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, or if the entity does not exist, this API returns an empty array.

```sh
adt list audit -n <developer-app-name> --type developer-app
```


## List all shared flow audit entries.
Lists audit entries for management operations for all shared flows in an organization.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against shared flows in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, or if the entity does not exist, this API returns an empty array.

For more about shared flows, see [Reusable shared flows](https://docs.apigee.com/api-platform/fundamentals/shared-flows). For information about listing audit entires for a specific shared flow, see List audit entries for a shared flow.


```sh
adt list audit --type sharedflow
```

### List a shared flow audit entries.

Lists audit entries for management operations for a shared flow in an organization.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against the specified app in an organization. The audit logs provide access to the actions (create, read, update, delete) executed on organizations.

If there are no audit entries, or if the entity does not exist, this API returns an empty array.

```sh
adt list audit -n <sharedflow-name> --type sharedflow
```


### List a user audit entries.

Lists audit entries for management operations for a user.

For every call made to the API, Apigee Edge logs an audit record. This API enables you to obtain a record of all API calls made against the specified user. The audit logs provide access to the actions (create, read, update, delete) executed on the user.

If there are no audit entries, o

```sh
adt list audit -n <user-email> --type user
```