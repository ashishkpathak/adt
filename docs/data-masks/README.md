# DATA MASK

Filter data from trace sessions.
Apigee Edge enables developers to capture message content to enable runtime debugging of APIs calls. In many cases, API traffic contains sensitive data, such as credit cards or personally identifiable health information (PHI) that needs to filtered out of the captured message content. Mask configurations enable you to specify data that will be filtered out of trace sessions. Masking configurations can be set globally (at the organization-level) or locally (at the API proxy level).

Create a data-mask using the methods described below. .


## LIST DATA MASKS

Lists data-masks for an organization.


### USAGE
```sh
adt list datamask 
```

Lists data-masks for an API proxy.

### USAGE
```sh
adt list datamask -a api-proxy-name
```

Gets an datamask definition for an organziation.

### USAGE
```sh
adt list datamask -n <maskconfig> --org
```

Gets an datamask definition <maskconfig> for an API <api-proxy-name>.

```sh
adt list datamask -n <maskconfig> -a <api-proxy-name>.
```

## CREATE DATA MASK


### USAGE

```sh
adt create datamask --help
```
