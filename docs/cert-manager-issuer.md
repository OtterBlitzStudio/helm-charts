# Cert Manager Issuer

This helm chart creates an Issuer or ClusterIssuer for [cert-manager](https://cert-manager.io/docs/).

## Installation

**You need to install [cert-manager](https://cert-manager.io/docs/installation/kubernetes/#installing-with-helm) before you can run this helm install. Moreover you need to change the email to your own adress.**


| Parameter | Description | Default |
| - | - | :-: |
| email | Your own email adress. The certificate is generated with this. You receive an email if the certificate becomes outdated. | "" |


## Template

```
helm install cert-manager-issuer obs/cert-manager-issuer --namespace cert-manager  --set email=xyz@provider.com 

```