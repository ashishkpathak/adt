# Installation



## Setup

<a href="../download">Download</a> the latest version of ADT for your platform. 

Setup ADT for your environment, by providing the following:

- Username 
- Password
- Organization Name.
- OAuth API endpoint for getting an access token.

ADT would use these to request an access token to invoke the management API. This is one time operation. There are two ways of initializing the tool. 

### USAGE

```sh

A.D.T
Initialise adt environment
Usage: adt init [-hV] [-p[=<password>]] [-c=<loginEndpoint>] [-o=<org>] [--org:env=<orgEnv>] [--password:env=<passwordEnv>] -u=<userName> [--url:env=<urlEnv>] [--username:env=<userNameEnv>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -c, --url=<loginEndpoint>
                           The OAuth endpoint.
                             Default: https://login.apigee.com/oauth/token
  -h, --help               Show this help message and exit.
  -o, --org=<org>          The organization name.
      --org:env=<orgEnv>   Read the OAuth URL from system environment variable <orgEnv>.
  -p, --password[=<password>]
                           The password.
      --password:env=<passwordEnv>
                           Read the password from system environment variable <passwordEnv>.
  -u, --username=<userName>
                           The username to use.
      --url:env=<urlEnv>   Read the password from system environment variable <urlEnv>.
      --username:env=<userNameEnv>
                           Read the username from system environment variable <userNameEnv>.
  -V, --version            Print version information and exit.
Exit Code:
Version 0.0.1
```

### Interactive Mode 

The tool would prompt for the password when invoked with -p option. 
### USAGE

```sh
adt init -u myusername@domain.com -o myorganization -c https://myorg.login.apigee.com/oauth/token -p
Enter value for --password (The password.):
```

This would interactively accept the password. If url is not provided it defaults to https://login.apigee.com/oauth/token

This generates a config  in ~/.aditi/aditi.conf with these values. It would then request for an access and refresh token from ADT_URL provided. The tokens would be stored in ~/.aditi/config.json


### Batch Mode 

When running ADT as a batch mode, these config parameters can be provided as system variables.


```sh
export ADT_USERNAME=myusername@domain.com.au
export ADT_PASSWORD=mypassword
export ADT_ORGANIZATION=myorganization
export ADT_URL=https://myorganization.login.apigee.com/oauth/token

adt init --org:env ADT_ORGANIZATION --username:env ADT_USERNAME --password:env ADT_PASSWORD --url:env ADT_URL
```


This generates a config  in ~/.aditi/aditi.conf with these values. It would then request for an access and refresh token from ADT_URL provided. The tokens would be stored in ~/.aditi/config.json





