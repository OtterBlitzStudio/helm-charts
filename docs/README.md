# OBS Helm Charts
### A monorepo for all helm charts of Otter Blitz Studio.

Those charts shall decrease complexity for deploying a distributed and secure [Nakama](https://heroiclabs.com/docs/nakama-download/) gameserver.

## Repo

```
helm repo add obs https://otterblitzstudio.github.io/helm-charts/
```
```
helm repo update
```

## Charts

### [Cert Manager Issuer](cert-manager-issuer.md)

This helm chart creates an Issuer or ClusterIssuer for [cert-manager](https://cert-manager.io/docs/).

### [GCP NFS PV](gcp-nfs-pv.md)

This helm chart creates a network file system on Google Cloud Platform and a Persistant Volumes to enable ReadWriteMany for the Nakama server.

### [Secure Distributed Nakama](secure-distributed-nakama.md)

This helm chart creates the Nakama gameserver with all resources (deployment, service, pvc, ingress).

***
