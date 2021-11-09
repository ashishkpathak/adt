# Virtual Host

## Create Virtual Host 
Creates a virtual host.

Virtual hosts let multiple domain names connect to the same host. A virtual host on Edge defines the domains and ports on which an API proxy is exposed, and, by extension, the URL that apps use to access an API proxy. A virtual host also defines whether the API proxy is accessed by using the HTTP protocol, or by the encrypted HTTPS protocol.

The request body content used to create a virtual host depends on whether you are using Edge for the Cloud or Edge for the Private Cloud. If you are using Edge for the Private Cloud, then it also depends on which version of Edge for the Private Cloud you are using. For a complete list of all options for the request body, see [Virtual host property reference](https://docs.apigee.com/api-platform/fundamentals/virtual-host-property-reference).


For example, a subset of request body properties are valid only for specific Edge for Private Cloud versions, as follows:

- ciphers and protocols properties are valid on Edge for Private Cloud version 4.15.07 and earlier
- properties array is valid on Edge for Private Cloud version 4.17.01 and later
- baseUrl property is valid on Edge for Private Cloud version 4.17.05 and later
- retryOptions and listenOptions properties are valid on Edge for Private Cloud version 4.18.01 and later

Updating a proxy to use the new virtual host

When you create a new API proxy, Edge automatically configures its ProxyEndpoint to use all available virtual hosts. If you create a new API proxy that should not be accessible over a particular virtual host, then you must edit the API proxy to remove that virtual host from its ProxyEndpoint.

If you created any API proxies before requesting the virtual host, then you must edit the API proxy to add the new virtual hosts to its ProxyEndpoint. Otherwise, the API proxy is not accessible by the virtual host. See Configuring an API proxy to use a virtual host.


### Usage  

```sh


```

## Update Virtual Host 
You must specify the complete description of the virtual host in the request body, not just the elements that you want to change. You can get the current virtual host properties, as described in Get a virtual host.

The request body used to create a virtual host depends on whether you are using Edge for the Cloud or Edge for the Private Cloud. If you are using Edge for the Private Cloud, then it also depends on which version of Edge for the Private Cloud you are using. For a complete list of all options for the request body, see [Virtual host property reference](https://docs.apigee.com/api-platform/fundamentals/virtual-host-property-reference).

For example, a subset of request body properties are valid only for specific Edge for Private Cloud versions, as follows:

- ciphers and protocols properties are valid on Edge for Private Cloud version 4.15.07 and earlier
- properties array is valid on Edge for Private Cloud version 4.17.01 and later
- baseUrl property is valid on Edge for Private Cloud version 4.17.05 and later
- retryOptions and listenOptions properties are valid on Edge for Private Cloud version 4.18.01 and later
  
### Usage  

## List Virtual Host 
Lists all virtual hosts in an environment. By default, two virtual hosts are available for each environment: default and secure


### Get details of virtual host 

Every environment has at least one virtual host that defines the HTTP settings for connection with the Apigee organization. All API proxies in an environment share the same virtual hosts. By default, two virtual hosts are available for each environment: default and secure.


### Usage  

## Delete Virtual Host

Deletes a virtual host.

Before you can delete a virtual host from an environment, you must update any API proxies that reference the virtual host to remove the reference. See [About virtual hosts](https://docs.apigee.com/api-platform/fundamentals/virtual-hosts) for more.


### Usage  
