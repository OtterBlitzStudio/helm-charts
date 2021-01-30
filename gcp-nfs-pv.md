# GCP NFS PV

This helm chart creates a network file system on Google Cloud Platform and a Persistant Volumes to enable ReadWriteMany for the Nakama server.

## Installation

> :warning: **You need to create a disk on gcp before you can intall this chart.**

*Example:*
```sh
gcloud compute disks create --size=10GB --zone=us-east1-b <disk-name>
```

### Values

| Parameter | Description | Default | Needs Change |
| - | - | :-: | :-: |
| diskName | The name of the disk which should be used for the nfs-server |  | X |
| cluster | The cluster path for all your services | svc.cluster.local | |
| pvStorage | The amount of storage size you want to use for your pv| 10Gi | |
| image | The image you want to use for your nfs-server | gcr.io/google_containers/volume-nfs:0.8 | |
| ports.nfs | The port for the server: nfs| 2049 | |
| ports.mountd | The port for the server: mountd| 20048 | |
| ports.mountd | The port for the server: rpcbind| 111 | |


## Template

```
helm install <project-name>-data  obs/gcp-nfs-pv -n <project-name> --set diskName=<disk-name>

```