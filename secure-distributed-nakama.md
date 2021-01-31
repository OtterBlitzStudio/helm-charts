# Secure Distributed Nakama

This helm chart creates the Nakama gameserver with all resources (deployment, service, pvc, ingress).

## Installation

### Values

> :warning: **Some values need to be replaced to install the helm chart successfully:**

| Parameter | Description | Default | Needs Change |
| - | - | :-: | :-: |
| ingress.serviceHost | Your url/DNS which you own and where the server should be reachable |  | X |
| pvc.name | The name of your persistant volume which needs to have ReadWriteMany as accessModes, check [GCP NFS PV](gcp-nfs-pv-md) for more information. |  | X |
| ingress.beta | If set to `true` you use Ingress for kubernetes version < 1.18.0 | true |  |
| ingress.cluster | If you are using cert-manager ClusterIssuer it is `true`, for Issuer `false` | true |  |
| ingress.class | Your ingress you want to use | nginx |  |
| ingress.adminHost | Your url/DNS which you own and where the admin UI should be reachable | false |  |
| ingress.certManagerIssuerName | The name of the ClusterIssuer/Issuer you are using | letsencrypt-production |  |
| pvc.size | The amount of storage size you use for your pvc | 100Mi |  |
| nakama.withPodInfo | If `true` it mounts some information about the pod where the nakama server is running  | true |  |
| nakama.port | The port where the server is running, (port-1) for grpc and (port+1) for admin ui| 7350 |  |
| nakama.replicas | How many replicas you want to create after installing | 3 |  |
| nakama.image | The image and version you want to use | heroiclabs/nakama:2.14.1 |  |
| nakama.resources.requests.memory | The memory the server should request from the node | 100Mi |  |
| nakama.resources.requests.cpu | The cpu the server should request from the node | 100Mi |  |
| nakama.resources.limits.memory | The max. memory the server should request from the node | 100Mi |  |
| nakama.resources.limits.memory | The max. cpu the server should request from the node | 100Mi |  |

### Secrets

> :warning: **Moreover you need to create an extra file for generating all required secrets.**

Create a directory with your project name where you create a .yaml file.
You need to replace the values "X" with your secrets decoded with **base64**.

:information_source: Don't use an online base64 decoder, instead do it from the command line. And save your secrets into something like [KeePass](https://keepass.info/) for better control.

```yaml
secrets:
  dbUser: X
  db: X
  socketServerKey: X
  sessionEncryptionKey: X
  runtimeHttpKey: X
  consolePassword: X
  consoleSigningKey : X
```


### Config (Optional)

You can configure your server with an extra config.yaml.
The `config:` is required, all other configuration parameters can be found [here](https://heroiclabs.com/docs/install-configuration/#example-file).

*Example:*
```yaml
config:
  socket:
    max_message_size_bytes: 10000
    max_request_size_bytes: 10000
    read_buffer_size_bytes: 10000
    write_buffer_size_bytes: 10000

  session:
    token_expiry_sec: 100000
```

## Template

```sh
helm install <project-name>  obs/secure-distributed-nakama -n <project-name> -f <project-name>-config.yaml  -f <project-name>-secrets.yaml  --set pvc.name=<project-name>-data --set ingress.serviceHost=<your-domain>

```