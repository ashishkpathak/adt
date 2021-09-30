# Installation

## Setup

Download the latest version of ADT for your platform. 

Setup ADT for your environment, by providing the following:

- Username 
- Password
- Organization Name.
- The OAuth API endpoint for getting an access token.


When running ADT as a batch mode, the above can be provided as system variables.


```sh
adt init --org:env --username:env --password:env --url:env
```


```sh
export ADT_USERNAME=myusername@domain.com.au
export ADT_PASSWORD=mypassword
export ADT_ORGANIZATION=myorganization
export ADT_URL=https://myorganization.login.apigee.com/oauth/token

adt init --org:env ADT_ORGANIZATION --username:env ADT_USERNAME --password:env ADT_PASSWORD --url:env ADT_URL
```


This would generate a config  in ~/.aditi/application.conf with these values. It would then request for an access and refresh token from ADT_URL provided. The tokens would be stored in ~/.aditi/config.json

```
adt init --org <org> --username <username> --url <url> --password
```

This would interactively accept the password. If url is not provided it defaults to https://login.apigee.com/oauth/token




