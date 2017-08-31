# BOSH release for SoftHSMv2

This BOSH release and deployment manifest deploy a cluster of softhsm.

* [Concourse CI](https://ci.starkandwayne.com/teams/main/pipelines/softhsm-boshrelease)
* Pull requests will be automatically tested against a bosh-lite (see `testflight-pr` job)

## Install

```
export BOSH_ENVIRONMENT=<bosh-alias>
export BOSH_DEPLOYMENT=softhsm
bosh deploy manifests/softhsm.yml --vars-store tmp/creds.yml \
  -v hsm-4digit-so-pin=1234 \
  -v hsm-4digit-user-pin=1234
```

If your BOSH has Credhub, then you can omit `--vars-store` flag. It is used to generate any passwords/credentials/certificates required by `manifests/softhsm.yml`.
