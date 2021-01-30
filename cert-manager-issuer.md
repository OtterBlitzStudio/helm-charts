# Cert Manager Issuer

This helm chart creates an Issuer or ClusterIssuer for [cert-manager](https://cert-manager.io/docs/).

## Installation

> :warning: **You need to install [cert-manager](https://cert-manager.io/docs/installation/kubernetes/#installing-with-helm) before you can run this helm install.**

**Moreover you need to change the email to your own adress.**


### Values

| Parameter | Description | Default | Needs Change |
| - | - | :-: | :-: |
| email | Your own email adress. The certificate is generated with this. You receive an email if the certificate becomes outdated. |  | X |
| normalIssuer | If set to ``true`` you won't create a ClusterIssuer. | false | |
| prod | If set to ``false`` you fetch the certificate from letsencrypt-staging | true | |
| name | The name of the certificate you will create. | letsencrypt-production | |
| class | The ingress you want to use with the certificate. | nginx | |


## Template

```
helm install cert-manager-issuer obs/cert-manager-issuer --namespace cert-manager  --set email=xyz@provider.com 

```