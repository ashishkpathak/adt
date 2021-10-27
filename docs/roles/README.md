# USER ROLE

Manage role-based access in Apigee Edge. User roles form the basis of role-based access in Apigee Edge.

Users are associated with one or more user roles. Each user role defines a set of permissions (GET, PUT, DELETE) on RBAC resources (defined by URI paths).

A user role is scoped to an organization.


## Create Operations

### USAGE

```sh
A.D.T
Operation on user roles.
Usage: adt create user-role [-hV] -;=<input> [-x=<hostPort>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -i, --user-role-config=<input>
                  Location of user role config.
  -h, --help      Show this help message and exit.
  -V, --version   Print version information and exit.
  -x, --http-proxy=<hostPort>
                  Use http proxy (host:port)
Version 1.0.0
```


### CREATE user role  
Creates one or more user roles in an organization.

After you create the role, you can use the following operations to add permissions to the role:

- Add permissions for multiple resources to a role.
- Add permissions for a single resource to a role.

Role names cannot contain special characters.

```sh
adt create user-role -i ../samples/user-role/create-test-role.json
```


## LIST OPERATIONS

### USAGE

```sh
A.D.T
Operation on user-roles.
Usage: adt list user-role [-hV] [--permissions] [-n=<name>] [--path=<path>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help          Show this help message and exit.
  -n, --name=<name>   The name of userrole.
      --path=<path>   The path.
      --permissions   List permissions for the userrole and path.
  -V, --version       Print version information and exit.
  -x, --http-proxy=<proxyHost>
                      Host:Port of the proxy server to use.
Version 1.0.0

```
#### List all user-roles in an organization.

```sh
adt list user-role
```

Sample response

```json
[ "user", "devadmin", "opsadmin", "orgadmin", "zoneadmin", "apimonitoringuser", "apimonitoringadmin" ]
```


#### List all permissions for a user-role


```sh
adt list user-role -n <role> --permissions
```

Sample response:

```json
{
  "resourcePermission" : [ {
    "organization" : "my-organization",
    "path" : "/",
    "permissions" : [ "get" ]
  }, {
    "organization" : "my-organization",
    "path" : "/applications",
    "permissions" : [ "get" ]
  }, {
    "organization" : "my-organization",
    "path" : "/apiproducts",
    "permissions" : [ "delete", "get", "put" ]
  }, {
    "organization" : "my-organization",
    "path" : "/developers",
    "permissions" : [ "delete", "get", "put" ]
  }, {
    "organization" : "my-organization",
    "path" : "/apps",
    "permissions" : [ "delete", "get", "put" ]
  }, {
    "organization" : "my-organization",
    "path" : "/companies",
    "permissions" : [ "delete", "get", "put" ]
  },{
    "organization" : "my-organization",
    "path" : "/deployments",
    "permissions" : [ "get" ]
  }, {
    "organization" : "my-organization",
    "path" : "/devPortalButton",
    "permissions" : [ "get" ]
  }, {
    "organization" : "my-organization",
    "path" : "/apimodels/*",
    "permissions" : [ ]
  }, {
    "organization" : "my-organization",
    "path" : "/environments/*/keyvaluemaps",
    "permissions" : [ ]
  } ]
}

```

#### List permissions of a user-role for a given path

```sh
adt list user-role -n <role> --permissions --path <path>
```

Sample response:

```json
{
  "organization" : "my-organization",
  "path" : "/environments",
  "permissions" : [ "get" ]
}
```

## QUERY

### USAGE




### Query userrole have permissions for a path.

Verifies that a user role's permission exists for a specific resource. Returns a value of true or false.

```sh
adt query user-role -n <role> --permission <permission> --path 
```

Sample response:

```json
{
  "value" : false
}
```

Verify if user role has the permission

```sh
adt query user -n <user> --role <role> 
```

## UPDATE

### USAGE

```sh
A.D.T
Operation on User Roles.
Usage: adt update user-role [-hV] [COMMAND]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help      Show this help message and exit.
  -V, --version   Print version information and exit.
Commands:
  permission  Operation on User Role Permissions.
Version 1.0.0
```

```sh
A.D.T
Operation on User Role Permissions.
Usage: adt update user-role permission [-hV] -i=<input> -n=<name> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help               Show this help message and exit.
  -i, --permission-config=<input>
                           Location of permissions config.
  -n, --role-name=<name>   Role name.
  -V, --version            Print version information and exit.
  -x, --http-proxy=<proxyHost>
                           Host:Port of the proxy server to use.
Version 1.0.0
```

### Update user-role.

User role permission can be updated using *adt update user-role permission* command. The input is JSON file. The file can contain an entry for single path, or multiple path, but not both.

```sh
adt update user-role permission -n test-role -i ../sample/user-role/test-role-multiple.json
```

Updating **single**, permission.json sample

```sh
adt update user-role permission -n test-role -i ../sample/user-role/test-role-single.json
```


```json
{
  "path": "/applications",
  "permissions": [
    "put",
    "get",
    "delete"
  ]
}
```


Updating **multiple**, the permission.json sample

```json
{
  "resourcePermission": [
    {
      "path": "/applications",
      "permissions": [
        "put",
        "get",
        "delete"
      ]
    },
    {
      "path": "/apiproducts",
      "permissions": [
        "put",
        "get",
        "delete"
      ]
    }
  ]
}
```
###  Add/Remove user from a role.


#### Usage 

```sh
A.D.T
Operation on User, to add/remove User Roles.
Usage: adt update user-role user [-hV] [--remove] -n=<roleName> -u=<userEmail> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help      Show this help message and exit.
  -n, --role-name=<roleName>
                  Role name.
      --remove    Remove a user role from user.
  -u, --user-email=<userEmail>
                  The user email.
  -V, --version   Print version information and exit.
  -x, --http-proxy=<proxyHost>
                  Host:Port of the proxy server to use.
Version 1.0.0

```
By default it adds the user to the role.

**Remove a user role from user.**

```sh
    adt update user-role user -n <user-email> --role <role> --remove
```

**Add a user role to user.**

```sh
    adt update user-role user -n <user-email> --role <role>
```


## DELETE 
### USAGE 

```sh
A.D.T
Operation on User Role.
Usage: adt delete user-role [-hV] [-n=<name>] [-x=<proxyHost>] [COMMAND]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help          Show this help message and exit.
  -n, --name=<name>   The name of userrole
  -V, --version       Print version information and exit.
  -x, --http-proxy=<proxyHost>
                      Host:Port of the proxy server to use.
Commands:
  permission  Operation on User Role Permissions.
Version 1.0.0
```
### Delete user-role

Deletes a role from an organization.

Roles can only be deleted when no users are assigned to the role. See Remove a user from a role.

```sh
adt delete user-role -n <user-role>
```


### Remove permission from user-role

Deletes a permission for a resource in the role specified. Permissions are case sensitive. Specify the permission as get, put, or delete.
The following removes the permission 'get' from path '/environments/sit4' for role 'test-role'.

```sh
adt delete user-role permission -n test-role -p get --path "/environments/sit4/"
```


