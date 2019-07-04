# ibm-ca-buildpack
CF Buildpack that imports IBM CA in JAVA keystore, so your application does not have to worry about reading/using the CA.

It also allows your app to be independent from the IBM Cloud specific way to provide the CA.

## Usage

Use multiple buildpacks when pushing:

```bash
cf push -b https://github.com/hsiliev/ibm-ca-buildpack -b https://github.com/cloudfoundry/java-buildpack.git#v4.19.1
```

or add in the manifest:

```yaml
    buildpacks:
      - https://github.com/hsiliev/ibm-ca-buildpack
      - https://github.com/cloudfoundry/java-buildpack.git#v4.19.1
```


## Details
This buildpack adds a `.profile` into your application. If you already have profile it will be overwritten.

The buildpack abuses one the restrictions documented in [How buildpacks work in CF](https://docs.cloudfoundry.org/buildpacks/understand-buildpacks.html), as it modifies the `build` directory!
