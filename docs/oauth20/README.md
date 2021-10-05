# OAuth 2.0 Token Management

## Query Access Token.

### Usage 

```sh
A.D.T
Operation on OAuth tokens.
Usage: adt query token [-hV] [-a=<accessToken>] [--app-id=<appId>] [--end-user=<endUserId>] [--limit=<limit>] [-r=<refreshToken>] [--start=<start>] [-t=<type>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --access-token=<accessToken>
                            The access token.
      --app-id=<appId>      Search for tokens based on developer App Id.
      --end-user=<endUserId>
                            Search for tokens based on ID of the user to whom the token was issued (the actual user of the client app).
  -h, --help                Show this help message and exit.
      --limit=<limit>       Number of results to return
                              Default: 10
  -r, --refresh-token=<refreshToken>
                            The refresh token.
      --start=<start>       Search starting from this token.
  -t, --type=<type>         The type of token. OAuth2.0 or OAuth1.0a
                              Default: OAuth2.0
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1

```

Query based on access token.

```sh
adt query token -a 4A12UW8TLoy5Cw8QRd5BY8mAGav0
```

Query based on the issued App (app-id)

```sh
adt query token --app-id cc7f8cf5-4d25-4f18-8f97-c17ba016bc67 --limit 100
```


## Update Access Token

### Usage

```sh
A.D.T
Operation on OAuth2.0 token.
Usage: adt update token [-hV] [--approve] [--cascade] [--revoke] -a=<accessToken> [-i=<config>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --access-token=<accessToken>
                            The access token.
      --approve             Set to true to approve. Defaults to true, unless revoke.
      --cascade             Flag that specifies whether the refresh token associated with the access token is also approved or revoked. Set to true to approve or revoke the refresh token.
                              Defaults to false.
  -h, --help                Show this help message and exit.
  -i, --token-config=<config>
                            Token attribute config.
      --revoke              Set to true to revoke. Defaults to false.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1
```

Update access token attributes/ scope. 

```sh
adt update token -a T1DYFXrRnIo1ZfSVk82w4f5El5JA -i ../../aditi/token-update/update.json
```

```json
{
    "attributes": [
        {
            "name": "im-id",
            "value": "5005123456789"
        },
        {
            "name": "subscriber_id",
            "value": "1500041900"
        }
    ],
    "scope":"SERVICE ADMIN"
}
```

## Delete Access Token

### Usage

```sh
A.D.T
Operation on OAuth 2.0 token.
Usage: adt delete token [-hV] [--cascade] [-a=<accessToken>] [--app-id=<appId>] [--end-user=<endUserId>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --access-token=<accessToken>
                            The access token.
      --app-id=<appId>      Search for tokens based on developer App Id.
      --cascade             Flag that specifies whether the refresh token associated with the access token is also approved or revoked. Set to true to approve or revoke the refresh token.
                              Defaults to false.
      --end-user=<endUserId>
                            Search for tokens based on ID of the user to whom the token was issued (the actual user of the client app).
  -h, --help                Show this help message and exit.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1
```

Delete an access token.

```sh
adt delete token -a iRPerx3Xxs5GZWest5k3ettavQG9
```

Sample response.


```json
{
  "apiProducts" : [ ],
  "app" : "3b0a6222-2757-483a-8802-086ab7499c9a",
  "appId" : "3b0a6222-2757-483a-8802-086ab7499c9a",
  "attributes" : [ ],
  "clientId" : "PKIKmQ9ZAMcyosAGGTmhhPf9QMl7UgAC",
  "createdAt" : 1633407386809,
  "expiresAt" : 1633493786809,
  "grantType" : "client_credentials",
  "issuedAt" : 1633407386809,
  "lastModifiedAt" : 1633407386809,
  "refreshCount" : 0,
  "scope" : "READ ADMIN WRITE",
  "status" : "revoked",
  "token" : "iRPerx3Xxs5GZWest5k3ettavQG9",
  "tokenType" : "BearerToken"
}
```

## Revoke all Access Token


### Usage
```sh

A.D.T
Operation on OAuth 2.0 token.
Usage: adt delete token [-hV] [--cascade] [-a=<accessToken>] [--app-id=<appId>] [--end-user=<endUserId>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --access-token=<accessToken>
                            The access token.
      --app-id=<appId>      Search for tokens based on developer App Id.
      --cascade             Flag that specifies whether the refresh token associated with the access token is also approved or revoked. Set to true to approve or revoke the refresh token.
                              Defaults to false.
      --end-user=<endUserId>
                            Search for tokens based on ID of the user to whom the token was issued (the actual user of the client app).
  -h, --help                Show this help message and exit.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1
```


Revokes all tokens issued to AppId (--app-id=<appId>).

```sh
adt delete token --app-id 3b0a6222-2757-483a-8802-086ab7499c9a
```