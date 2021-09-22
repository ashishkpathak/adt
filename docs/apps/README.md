# APPS
## CREATE APP
Creates an app associated with a developer, associates the app with an API product, and auto-generates an API key for the app to use in calls to API proxies inside the API product.

The name is the unique ID of the app that you can use in Edge API calls. The DisplayName (set with an attribute) is what appears in the Edge UI. If you don't provide a DisplayName, the name is used.

The keyExpiresIn property sets the expiration on the API key. If you don't set a value or set the value to -1, the API key never expires.
Ensure optimal API product and app security

An organization-level property, features.keymanagement.disable.unbounded.permissions, strengthens the security of API products in verifying API calls. When the property is set to true, the following features are enforced.

    App creation: When creating a developer or company app, the Edge API requires that the app be associated with an API product. (The Edge UI already enforces this.)

    API product configuration: To create or update an API product, the API product must include at least one API proxy or a resource path in its definition.

    Runtime security: API calls are rejected by an API product in the following situations:

        An API product doesn't include at least one API proxy or resource path.

        If the flow.resource.name variable in the message doesn't include a resource path that the API product can evaluate.

        If the app making the API call isn't associated with an API product.

Note: Setting this organization property requires system administrator privileges. Edge for Private Cloud system administrators can add this property when updating organization properties. If you are an Edge for Public Cloud user, contact Apigee Support to set the organization property

### USAGE

```sh
adt create app --help
```

```sh
Operation on App.
Usage: adt create app [-dhV] [-e=<env>] -n=<name> [-p=<input>]
                           [-x=<hostPort>]
  -h, --help                Show this help message and exit.
  -n, --api-name=<name>     The name of App.
  -p, --proxy-dir=<input>   Location of app directory or bundled proxy zip
                              file.
  -V, --version             Print version information and exit.
  -x, --http-proxy=<hostPort>
                            Use http proxy (host:port)
```                            
  
Note: Proxies using the create command, get created by not deployed. To create and deploy proxies, refer to below documentation.

#### Import an App directory.

Import an App configuration stored on local machine as following directory structure.


```sh
adt create app -n <api-proxy-name> --proxy-dir <proxy-location>
```

Example

```sh
adt create app -n api-httpbin-proxy --proxy-dir ../api-httpbin-proxy/
```

  The structure of api-httpbin-proxy as an example is

```sh
├── api-httpbin-v1
│   └── app
│       ├── api-httpbin-v1.xml
│       ├── policies
│       ├── proxies
│       │   └── default.xml
│       └── targets
│           └── default.xml
```

#### Import a zipped bundle

Import an App bundle stored as a zip file on your local machine to your organization on Edge by doing the following.

```sh
adt create app -n api-httpbin-proxy --proxy-dir ../api-httpbin-proxy.zip
```

NOTE: ADT can take **relative** and **absolute** paths.

Optionally the created proxy can be deployed to environment 'test'. For example

```sh
adt create app -n api-httpbin-proxy --proxy-dir ../api-httpbin-proxy.zip -d -e test
```

## QUERY App

Lists all apps created by a developer in an organization. Optionally, you can expand the response to include the profile for each app.

With Apigee Edge for Public Cloud:

    A maximum of 100 developer apps are returned per API call.
    You can paginate the list of developer apps returned using the startKey and count query parameters.

## UPDATE App
Approves, revokes, or generates an API key for a developer app.

To approve or revoke the API key for a developer app, set status to approve or revoke in the request body.

Note: As a convenience, you can call the API with the action query parameter set to approve or revoke (with no request body) and set the Content-type header to application/octet-stream. In this case, the HTTP status code for success is: 204 No Content

To generate a new consumer key and consumer secret for the developer app, pass the required details, such as API products, in the request body. Rather than replace an existing key, the API generates a new key.

For example, if you're using API key rotation, you can generate new keys with expiration times that overlap keys that will be out of rotation when they expire. You might also generate a new key/secret if the security of the original key/secret is compromised. After the new API key is generated, multiple key pairs will be associated with a single app. Each key pair has an independent status (revoked or approved) and an independent expiration time. Any non-expired, approved key can be used in an API call. You should revoke an API key that has been compromised.

Note: You must include all current attribute and callback values in the payload; otherwise, the existing values are removed.

If you want to set the consumer key and consumer secret rather than having Edge generate them randomly, see Import existing consumer keys and secrets. (However, that API does not let you set an expiration time.)

### USAGE


