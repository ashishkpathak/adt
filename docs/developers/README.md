# Developer

## Create Developer

### Usage

```sh
A.D.T
Operation on Developer.
Usage: adt create developer [-hV] -i=<input> [-x=<hostPort>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help                 Show this help message and exit.
  -i, --dev-config=<input>   The create developer configuration file.
  -V, --version              Print version information and exit.
  -x, --http-proxy=<hostPort>
                             Use http proxy (host:port)
Version 1.0.1


Exit: 0
```

#### Create a developer using config json.
```sh

adt create developer -i ../sample/developer/developer.json
```

Sample config for developer

```json
{
    "email": "apideveloper@yopmail.com",
    "firstName": "API",
    "lastName": "Developer",
    "userName": "apideveloper@yopmail.com",
    "attributes": [
      {
        "name": "developer-group",
        "value": "DT"
      }
    ]
  }
```

## List Developer


### Usage

```sh
A.D.T
Operation on Developer.
Usage: adt list developer [-AehV] [-a=<attributeName>] [-c=<count>] [-n=<email>] [-s=<startKey>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -a, --attribute-name=<attributeName>
                           List by attribute.
  -A, --list-attribute     List by attribute.
  -c, --count=<count>      The number of products to return in API call.
  -e, --expand             To view expanded form of products
  -h, --help               Show this help message and exit.
  -n, --email=<email>      List by email.
  -s, --start=<startKey>   The name of API product to start displaying from.
  -V, --version            Print version information and exit.
  -x, --http-proxy=<proxyHost>
                           Host:Port of the proxy server to use.
Version 1.0.1


Exit: 0
```

### List all developers

```sh
adt list developer -e
```

### List developer with email address

```sh
adt list developer -n apideveloper@domain.com
```

Sample response
```json
{
  "apps" : [ "app-httpbin" ],
  "email" : "apideveloper@yopmail.com",
  "firstName" : "API",
  "lastName" : "Developer",
  "userName" : "apideveloper@yopmail.com",
  "organizationName" : "company-enterprise-nonprod",
  "status" : "active",
  "createdAt" : 1634268077526,
  "lastModifiedAt" : 1634268077526,
  "createdBy" : "api.manager@company.com",
  "lastModifiedBy" : "api.manager@company.com",
  "developerId" : "cadc2441-9dbd-44dd-9fbe-f35d28773d56",
  "attributes" : [ {
    "name" : "developer-group",
    "value" : "DT"
  } ]
}
```

### List all attribures of developer

```sh
adt list developer -n apideveloper@domain.com -A
```

Sample response

```json
{
  "attribute" : [ {
    "name" : "developer-group",
    "value" : "DT"
  } ]
}
```

### List an attribure of developer

```sh
adt list developer -n apideveloper@domain.com -a developer-group
```

Sample response.

```json

{
  "name" : "developer-group",
  "value" : "DT"
}
```


## Update Developer

### Usage
```sh
A.D.T
Operation on Developer.
Usage: adt update developer [-hV] [--disable] [--enable] [-a=<attributeName>] [-i=<input>] -n=<email> [-v=<attributeValue>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -a, --attribute-name=<attributeName>
                        The product attribute name whose value to update.
      --disable         Inactivate the user.  If you set a developer's status to inactive, the API keys assigned to the developer's apps are no longer valid even though keys
                          continue to show a status of "Approved".
      --enable          Set the status of user as 'Active'.
  -h, --help            Show this help message and exit.
  -i, --input=<input>   Location of config file. The config file can be attribute JSON or complete developer JSON.
  -n, --name=<email>    The name of API proxy.
  -v, --attribute-value=<attributeValue>
                        The product attribute value to use.
  -V, --version         Print version information and exit.
  -x, --http-proxy=<proxyHost>
                        Host:Port of the proxy server to use.
Version 1.0.1


Exit: 0

```

#### Enable developer account.

```sh

adt update developer -n apideveloper@yopmail.com --enable
```

Update developer profile

```sh
adt update developer -n apideveloper@yopmail.com -i ../sample/developer/update-developer.json
```

## Delete Developer

```sh
A.D.T
Operation on Developer.
Usage: adt delete developer [-hV] [-a=<attribute>] -n=<name> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -a, --attribute-name=<attribute>
                      The attribute to delete.
  -h, --help          Show this help message and exit.
  -n, --name=<name>   Developer email address.
  -V, --version       Print version information and exit.
  -x, --http-proxy=<proxyHost>
                      Host:Port of the proxy server to use.
Version 1.0.1


Exit: 0

```
