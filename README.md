# Jenkinsfile

Para utilizar credenciales desde kubernetes ver los [ejemplos](https://jenkinsci.github.io/kubernetes-credentials-provider-plugin/examples/) aqui descritos, asi como como [inyectarlos](https://docs.cloudbees.com/docs/cloudbees-ci/latest/cloud-secure-guide/injecting-secrets) desde Jenkins. Tambien en la [documentacion oficial](https://www.jenkins.io/doc/book/pipeline/syntax/#environment) se puede encontrar buena informacion.

## Para utilizar credenciales almacenadas en un Secret en Openshift
El secreto deben haber sido creado de la siguiente manera:

```yaml
# Pasando directamente los datos por la terminal
$ oc create secret generic pipeline-credentials --from-literal=user=kubeadmin --from-literal=pass_prod_lc=S3cr3t0! --from-literal=pass_prod_cn=Sup3rsecret0 --namespace=jenkis-app

# Cifrando con base64 los valores para las variables en cuestion
$ echo -n 'super-secret-password' | base64
$ oc create -f secret-creds.yaml
$ cat secret-creds.yaml
---
kind: Secret
apiVersion: v1
metadata:
  name: pipeline-credentials-1
  namespace: jenkins-app
  labels:
    credential.sync.jenkins.openshift.io: 'true'
    jenkins.io/credentials-type: usernamePassword
  annotations:
    jenkins.io/credentials-description: certificate_credential_from_Kubernetes
data:
  password: U3VwM3JzZWNyZXQw
  username: a3ViZWFkbWlu
type: Opaque

```

Asegurate de crear un BuildConfig apuntando al repo:

```yaml
apiVersion: build.openshift.io/v1
kind: BuildConfig
metadata:
  name: my-build
  namespace: jenkins-app
spec:
  source:
    git:
      ref: master
      uri: 'https://github.com/lorcopotia/sample-app-for-jenkins.git'
    type: Git
  strategy:
    type: JenkinsPipeline
    jenkinsPipelineStrategy:
      jenkinsfilePath: Jenkinsfile
      env: []
```

Agregar el trigger correspondiente:

```shell
$ oc set triggers bc my-build --from-github


```
