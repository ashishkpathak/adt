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

## UPDATE App
Approves, revokes, or generates an API key for a developer app.

To approve or revoke the API key for a developer app, set status to approve or revoke in the request body.

Note: As a convenience, you can call the API with the action query parameter set to approve or revoke (with no request body) and set the Content-type header to application/octet-stream. In this case, the HTTP status code for success is: 204 No Content

To generate a new consumer key and consumer secret for the developer app, pass the required details, such as API products, in the request body. Rather than replace an existing key, the API generates a new key.

For example, if you're using API key rotation, you can generate new keys with expiration times that overlap keys that will be out of rotation when they expire. You might also generate a new key/secret if the security of the original key/secret is compromised. After the new API key is generated, multiple key pairs will be associated with a single app. Each key pair has an independent status (revoked or approved) and an independent expiration time. Any non-expired, approved key can be used in an API call. You should revoke an API key that has been compromised.

Note: You must include all current attribute and callback values in the payload; otherwise, the existing values are removed.

If you want to set the consumer key and consumer secret rather than having Edge generate them randomly, see Import existing consumer keys and secrets. (However, that API does not let you set an expiration time.)

### Usage

```sh
A.D.T
Operation on App.
Usage: adt update app [-hV] [--company] [-a=<attributeName>] [-i=<id>] [-l=<appConfigLocation>] [-n=<name>] [-t=<status>] [-v=<attributeValue>] [-x=<proxyHost>] [COMMAND]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --attribute-name=<attributeName>
                            The app attribute name.
      --company             Is company app.
  -h, --help                Show this help message and exit.
  -i, --id=<id>             The email address if developer app or company name if company app.
  -l, --app-config=<appConfigLocation>
                            The App config location. Can be app update or attribute update config. You must include all current attribute, API product, and callback values
                              in the payload along with any changes you want to make; otherwise, the existing values are removed. To display the current values, use list app.
  -n, --name=<name>         The app name.
  -t, --status=<status>     The status of app. Approved or Revoked
  -v, --attribute-value=<attributeValue>
                            The app attribute value.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Commands:
  key  Operation on App Keys.
Version 0.0.1

```

#### Update App
Add new credentials with new API products and attributes.

```sh
adt update app -i apideveloper@yopmail.com -n app-httpbin -l ../../aditi/app-httpbin/app-httpbin-update.json
```

This would update all the attributes, callback url.
Sample api-httpbin-update.json 

```json
{
    "apiProducts": [
        "aprod-httpbin-v1","aprod-httpbin-v2"
    ],
    "attributes": [
        {
            "name": "DisplayName",
            "value": "ADT-Demo-App"
        },
        {
            "name": "Notes",
            "value": "Demo httpbin app."
        },
        {
            "name": "PlayGround",
            "value": "Hockey-123"
        },
        {
            "name": "YeAttrib",
            "value": "attrib -xa -cb"
        }
    ],
    "callbackUrl": "http://callback-2.test.optusnet.com.au",
    "name": "app-httpbin",
    "scopes": [],
    "status": "approved"
}
```

## UPDATE App Key

## USAGE

```sh
Operation on App Keys.
Usage: adt update app key [-hV] [--approve] [--company] [--revoke] [-c=<productConfig>] -i=<id> -k=<key> -n=<appName> [-p=<product>] [-t=<status>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
      --approve              Approve the API Key or API Product. No other parameter required.
  -c, --product-config=<productConfig>
                             The config containing the attributes and products.
      --company              Is company app.
  -h, --help                 Show this help message and exit.
  -i, --id=<id>              The email address if developer app or company name if company app.
  -k, --key=<key>            The client  key
  -n, --app-name=<appName>   The app name.
  -p, --api-product=<product>
                             The api product.
      --revoke               Revoke the API Key or API Product. No other parameter required.
  -V, --version              Print version information and exit.
  -x, --proxy=<proxyHost>    Host:Port of the proxy server to use.
```

To revoke or approve App key. This would revoke the consumer key or app <app-name> of developer <developer-email>

```sh 
adt update app key -i <developer-email> -n <app-name> -k <consumer-key>  --revoke
```

To revoke or approve an api-products associated with the app key.

```sh
adt update app key -i <developer-email> -n <app-name> -k <consumer-key> -p <api-product> --revoke 
```

To update api-products or attributes associated with the app key.

```sh
adt update app key -i <developer-email> -n <app-name> -k <consumer-key> --product-config <product-confiig>
```


## LIST App


Lists all apps created by a developer in an organization. Optionally, you can expand the response to include the profile for each app.

With Apigee Edge for Public Cloud:

    A maximum of 100 developer apps are returned per API call.
    You can paginate the list of developer apps returned using the startKey and count query parameters.
### USAGE

```sh
Operation on App.
Usage: adt list app [-AehV] [--company] [-a=<attribute>] [--app-id=<appId>] [-c=<count>] [-i=<id>] [-n=<name>] [-s=<startKey>] [-t=<status>] [-v=<attributeValue>] [-x=<proxyHost>] [COMMAND]

  -a, --attribute-name=<attribute>
                            The app attribute name.
  -A, --list-attributes     List the attributes.
      --app-id=<appId>      The App Id
  -c, --count=<count>       The number of apps to return.
      --company             Is company app.
  -e, --expand              To view expanded form of app.
  -h, --help                Show this help message and exit.
  -i, --id=<id>             The email address if developer app or company name if company app.
  -n, --name=<name>         The app name.
  -s, --start-key=<startKey>
                            The AppId to start displaying from.
  -t, --status=<status>     The status of app. Approved or Revoked
  -v, --attribute-value=<attributeValue>
                            The app attribute value.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Commands:
  key  Operation on App Keys.
```

List all apps (developer app), for company apps pass in --company  option. This would return the app-Id of the app.  To see the expanded form use the expanded -e option. To  list them with status approved or revoked, use the -t option.


```sh
adt list app 
```


```sh
adt list app -e
```


```sh
adt list app -i <developer-email-address>
```


## LIST App Key (Credentials)

### USAGE

```sh
Operation on App Keys.
Usage: adt list app key [-hV] [--company] -i=<id> -k=<key> -n=<appName> [-p=<product>] [-t=<status>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
      --company              Is company app.
  -h, --help                 Show this help message and exit.
  -i, --id=<id>              The email address if developer app or company name if company app.
  -k, --key=<key>            The key
  -n, --app-name=<appName>   The app name.
  -p, --api-product=<product>
                             The api product.
  -t, --status=<status>      The status of app. Approved or Revoked
  -V, --version              Print version information and exit.
  -x, --proxy=<proxyHost>    Host:Port of the proxy server to use.
```

### List keys/credentials for a app.

```sh
adt list app key -i <developer-email> -n <app-name> -k <customer-key>
```


## Query App

### Usage

```sh
A.D.T
Operation on App.
Usage: adt query app [-hV] [--company] [-a=<attributeName>] [-c=<limit>] [-k=<customerKey>] [-n=<name>] [-v=<attributeValue>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -a, --attribute-name=<attributeName>
                            Search app with attribute name
  -c, --limit=<limit>       Number of results to return. Default 10.
      --company             Is company app.
  -h, --help                Show this help message and exit.
  -k, --key=<customerKey>   Search app with customer key
  -n, --name=<name>         The name of API proxy.
  -v, --attribute-value=<attributeValue>
                            Search app with attribute value
  -V, --version             Print version information and exit.
  -x, --http-proxy=<proxyHost>
                            Host:Port of the proxy server to use.
Version 1.0.0

```


Query for app which contain text in their name.  
```sh
adt query app -n <text>
```

Query for app which has an attribute name

```sh
adt query app -a <attribute-name> 
```

Query for app which has an attribute value. 

Note: The attribute value can be for any attribute name, not necessarly the queried attribute name.

```sh
adt query app -a <attribute-name> -v <attribute-value>
```

Query for an App with consumer key 

```sh
adt query app -k <consumerkey>
```