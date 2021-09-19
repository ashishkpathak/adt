# ADT
## _Apigee Edge Deployment Tool_

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

ADT is command-line tool for deploying Apigee resources like API proxies, API products, Apps, Shared-flows, KVMs to your Apigee Edge public or private cloud.

ADT can be used to create, deploy, list.

- [API Proxy](api-proxy)
- [API Products](api-products)
- [Shared Flows](shared-flows)
- [KVM](key-value-maps)
- [Environments](environments)
- [Developers](developers)
- [Developer Apps](apps)
- [Company Apps](apps)
- [Users](users)
- [Roles](roles)
- [Alerts](alerts)
- [Analytics](analytics)
- [Reports](reports)
- [Cache](cache)
- [Target Servers](target-servers)
- [Policies](policies)
- [Resources](resources)
- [Virtual Hosts](virtual-hosts)
- [Stats](stats)
- [Organizations](organizations)
- [Audit](audit)
- ✨Magic ✨

## Features

- Create an empty API Proxy template, have it created and deployed to Apigee Edge.
- Validate your proxies/shared-flow policies for XML syntax and consistences.
- Download API proxy revisions.
- Query OAuth2.0 tokens
- Export proxies, shared-flows, products.

As [Alexender Pope] writes

> Nature and Nature's laws lay hid in night:
> God said, Let Newton be! and all was light.


## Tech


- [API Proxy](create) - API Proxies.
- [API Product](create) - Products.



## Installation

ADT

Install the command line tool and init your environment.

```sh
adt init --login
```

For production environments...



## Help

```sh
A.D.T
Apigee Deployment Tool
Usage: adt [-hV] [COMMAND]
ADT is a fast, secure and reliable way to manage your proxies on Apigee.
  -h, --help      Show this help message and exit.
  -V, --version   Print version information and exit.
Commands:
  help    Displays help information about the specified command
  create  Create operations on various apigiee modules (apps, developer,
            proxies, products etc)
  deploy  Deploy apiproxies and shared-flows.
  delete  Remove various modules.
  list    List operations on proxies/kvm/products etc.
  query   Query OAuth 2.0 tokens.
  update  Update apps, developer, proxies, products etc
Exit Codes:
[Copyright 2021]Version 1.0.0
```


#### Building for source

For production release:


```

## License
All Rights Reserved.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
