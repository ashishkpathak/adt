# Key Value maps

## CREATE KVM

### Usage

```sh
A.D.T
Operation on KVM.
Usage: adt create kvm [-hoV] [-a=<api>] [-e=<env>] -p=<input> [-r=<revision>] [-x=<hostPort>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --api=<api>            KVM scoped to API.
  -e, --env=<env>            KVM scoped to environment.
  -h, --help                 Show this help message and exit.
  -o, --org                  KVM scoped to organization.
  -p, --kvm-config=<input>   Location of KVM config file.
  -r, --revision=<revision>  KVM scoped to API revision.
  -V, --version              Print version information and exit.
  -x, --http-proxy=<hostPort>
                             Use http proxy (host:port)
```

Create a KVM scoped to an environment.

```sh
adt create kvm --env dev -p ../../../kvm-demo-adt/kvm-demo-adt.json
```

Sample response 

```json
{
  "encrypted" : false,
  "entry" : [ {
    "name" : "mock-uri",
    "value" : "https://mockapi.com/pet/421"
  } ],
  "name" : "kvm-demo-adt"
}
```

Create a KVM scoped to an organization/API revision.

<img src="../../caution-60x52.png"/>Work In Progress

## LIST KVM

Lists the key value maps (KVMs) for an environment/API/Organization.
### Usage

```sh
A.D.T
Operation on KVM.
Usage: adt list kvm [-hkoV] [-a=<api>] [-e=<env>] [-n=<name>] [-r=<revision>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --api=<api>           KVM scoped to API.
  -e, --env=<env>           KVM scoped to environment.
  -h, --help                Show this help message and exit.
  -k, --keys                Key of KVM.
  -n, --name=<name>         The name of KVM.
  -o, --org                 KVM scoped to organization.
  -r, --revision=<revision> KVM scoped to API revision.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1
```

List KVM for an environment 'test'
```sh
adt list kvm --env test
```

```json
[ "kvm-http-default" ]
```

Get details of KVM (-n) scoped to environment (-e)

```sh
adt list kvm --env dev -n kvm-http-default
```
Sample response

```json
{
  "encrypted" : false,
  "entry" : [ {
    "name" : "oauth_refreshtoken_expires",
    "value" : "100000000"
  }, {
    "name" : "oauth_accesstoken_expires",
    "value" : "86400000"
  } ],
  "name" : "kvm-http-default"
}
```


Get keys of KVM (-n) scoped to environment (-e)

```sh
adt list kvm --env dev -n kvm-http-default -k
```

```json
[ "oauth_refreshtoken_expires", "oauth_accesstoken_expires" ]
```

## Update KVM

### USAGE

```sh
A.D.T
Operation on KVM.
Usage: adt update kvm [-hoV] [-a=<api>] [-e=<env>] [-k=<key>] -n=<name> [-p=<input>] [-r=<revision>] [-v=<value>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --api=<api>           KVM scoped to API.
  -e, --env=<env>           KVM scoped to environment.
  -h, --help                Show this help message and exit.
  -k, --key=<key>           The key in Map.
  -n, --name=<name>         The name of KVM.
  -o, --org                 KVM scoped to organization.
  -p, --entries-config=<input>
                            Location of KVM entries file. Entry in format {"name":"K1","value":"V1"}
  -r, --revision=<revision> KVM scoped to API revision.
  -v, --value=<value>       The value of the key.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1
```


### Update value for a key 


```sh
adt update kvm --env dev -n kvm-apigee-demo  -k user-id -v john.kid2
```

### Update KVM with key/value pairs in config file.

<img src="../../caution-60x52.png"/>Work In Progress


## Delete KVM

### USAGE

```sh
A.D.T
Operation on KVM.
Usage: adt delete kvm [-hoV] [-a=<api>] [-e=<env>] [-k=<key>] -n=<name> [-r=<revision>] [-x=<proxyHost>]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -a, --api=<api>           KVM scoped to API.
  -e, --env=<env>           KVM scoped to environment.
  -h, --help                Show this help message and exit.
  -k, --key=<key>           KVM key to delete.
  -n, --name=<name>         The name of KVM.
  -o, --org                 KVM scoped to organization.
  -r, --revision=<revision> KVM scoped to API revision.
  -V, --version             Print version information and exit.
  -x, --proxy=<proxyHost>   Host:Port of the proxy server to use.
Exit Code:
Version 0.0.1
```

Delete KVM entry for environment scoped KVM.

```sh
adt delete kvm --env test -n kvm-apigee-demo -k  user-id 
```

Delete KVM for environment scoped KVM.

```sh
adt delete kvm --env test
```


Delete KVM for API scoped KVM.

```sh
adt delete kvm --api api-httpbin-proxy-v1 -r 4 -n kvm-apigee-demo
```

Delete KVM for ORG scoped KVM.

```sh
adt delete kvm --org -n kvm-apigee-demo
```

Delete KVM entry for Organization and API scoped KVM.

<img src="../../caution-60x52.png"/>Work In Progress