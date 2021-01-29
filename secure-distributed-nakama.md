# Secure Distributed Nakama

This helm chart creates the Nakama gameserver with all resources (deployment, service, pvc, ingress).

## Installation

**Some values need to be replaced to install the helm chart successfully:**

| Parameter | Description | Default |
| - | - | :-: |
| ingress.serviceHost | Your url/DNS which you own and where the server should be reachable | TODO |
| pvc.name | The name of your persistant volume which needs to have ReadWriteMany as accessModes, check [GCP NFS PV](gcp-nfs-pv-md) for more information. | TODO |

**Moreover you need to create a secret.yaml:**

//TODO


*There are some optinal values, which you could overwrite check them [here](https://github.com/OtterBlitzStudio/secure-distributed-nakama/blob/main/values.yaml).*

## Template

```
helm install <project-name> -namespace <project-name> obs/secure-distributed-nakama -f server-config.yaml  -f values.yaml  --set pvc.name=<project-name>-data --set ingress.serviceHost=<your-domain>

```