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
- [[Roles](roles)
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

Dillinger uses a number of open source projects to work properly:

- [API Proxy](create) - API Proxies.
- [API Product](create) - Products.
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Installation

ADT requires [JRE](https://openjdk.java.net/) v11+ to run.

Install the command line tool and init your environment.

```sh
cd adt
$adt> adt init --login
```

For production environments...

```sh
npm install --production
NODE_ENV=production node app
```


## Development

Want to contribute? Great!

ADT uses Java 11.

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```


```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**
