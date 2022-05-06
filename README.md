# Openshift 4 Code Ready Container Setup

## Setup
- Create or reuse openshift account
- Download crc [https://console.redhat.com/openshift/create/local](https://console.redhat.com/openshift/create/local) and download pull secret
- Setup: `$ crc setup`
- Set memory `crc config set memory 12288`
- Add pull secret when asked
- Dashboard available at [https://console-openshift-console.apps-crc.testing/add/all-namespaces](https://console-openshift-console.apps-crc.testing/add/all-namespaces)

## Initial Deploy Mockserver
- Login via token (top right in the openshift ui, "choose copy login command")
- `$ oc new-project dev`
- `$ cd mockserver`
- `$ oc new-build --name mockserver --binary --strategy docker`
- `$ oc start-build mockserver --from-dir=. --follow`
- `$ oc new-app mockserver`
- `$ oc expose svc/node`
