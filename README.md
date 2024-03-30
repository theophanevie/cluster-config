# Cluster config

The umbrella charts for my personal Kubernetes cluster.

Most of the tools are completely overkill, but this allows me to test various apps of https://landscape.cncf.io/.

## SealedSecrets

#### Encrypt

Fetch `cert.pem` :
```shell
$ kubeseal --controller-name=clust-config-sealed-secrets --controller-namespace=default --fetch-cert > cert.pem
```
Encrypt : 
```shell
$ kubeseal --format=yaml --cert /path/to/cert.pem < /path/to/secrets-unsealed.yaml > /path/to/secrets-sealed.yaml
```

#### Decrypt

Docs : https://github.com/bitnami-labs/sealed-secrets?tab=readme-ov-file#how-can-i-do-a-backup-of-my-sealedsecrets

Fetch `main.key` :
```shell
$ kubectl get secret -n default sealed-secrets-keyxxxx -o yaml > main.key 
```
Decrypt
```shell
$ kubeseal --recovery-unseal --recovery-private-key main.key < /path/to/secrets-sealed.yaml > /path/to/secrets-unsealed.yaml
```

### TODO

#### Sealed secrets

- Remove fullname harcoding

#### OpenFeatures

- Test https://openfeature.dev/docs/reference/technologies/server/python

#### Loki

- Clean PVC
