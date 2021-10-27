# USER


## CREATE USER 

Creates a global user.
### Usage
```sh

A.D.T
Operation on User.
Usage: adt create user [-hV] -i;=<input> [-x=<hostPort>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help      Show this help message and exit.
      -i;, --user-config=<input>
                  Location of user config.
  -V, --version   Print version information and exit.
  -x, --http-proxy=<hostPort>
                  Use http proxy (host:port)
Version 1.0.0
```

#### Create a user.

After you create the user in an organization, you must assign the user to a role in an organization. Roles determine the access rights of the user on Edge. The user cannot sign in to the Edge UI, and does not appear in the list of users in the Edge UI, until you assign it to a role in an organization. See Add a user to a role.

```sh
adt create user -i ../samples/user/create-user.json 
```


## LIST USER 

Gets user details.

### Usage

```sh
A.D.T
Operation on user.
Usage: adt list user [-hV] [--global] [-n=<name>] [--role=<role>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
      --global        Indicator to get global user.
  -h, --help          Show this help message and exit.
  -n, --name=<name>   The user email.
      --role=<role>   The user-role. If not global.
  -V, --version       Print version information and exit.
  -x, --http-proxy=<proxyHost>
                      Host:Port of the proxy server to use.
Version 1.0.0
```

List all global user.

```sh
adt list user --global 
```

List all users, belonging to user-roles within the organization. This internally iterates over all roles.

```sh
adt list user 
```

List all users with the role opsadmin, in the organization.

```sh
adt list user --role opsadmin 
```

## UPDATE USER 

Updates a user.

### Usage


```sh
A.D.T
Operation on User.
Usage: adt update user [-hV] [--unlock] [-i=<input>] -n=<name> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help                Show this help message and exit.
  -i, --user-config=<input> Location of user config.
  -n, --user-email=<name>   User email.
      --unlock              Unlocks the user.
  -V, --version             Print version information and exit.
  -x, --http-proxy=<proxyHost>
                            Host:Port of the proxy server to use.
Version 1.0.0

```

**Update a user.**

When calling this operation.

- You must pass first name, last name, and email address to the call, even if you are not changing the values.
- The password is the only optional property. Only specify password when you want to change the user's password.

To view the current information about a user, see Get user.

```sh
adt update user -n <user-email> -i ../../sample/user/update-user.json
```

**Unlock a user.**

```sh
adt update user -n <user-email> --unlock
```


## DELETE USER 

Deletes a user.
### Usage

```sh

A.D.T
Operation on user.
Usage: adt delete user [-hV] -n=<name> [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your entities on Apigee.
  -h, --help                Show this help message and exit.
  -n, --user-email=<name>   The user email.
  -V, --version             Print version information and exit.
  -x, --http-proxy=<proxyHost>
                            Host:Port of the proxy server to use.
Version 1.0.0

```
#### Delete a user.

```sh
adt delete user -n user@domain.com 
```




//list global users.
adt list users --global


//list global users.
adt list users --global -n <useremail>

//update global users.
adt update users --global -n <useremail>


//delete global users.
adt delete users --global -n <useremail>

//delete global users.
adt update users --global -n <useremail> --unlock