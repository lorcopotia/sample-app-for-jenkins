# Jenkinsfile

Para utilizar credenciales desde kubernetes ver los [ejemplos](https://jenkinsci.github.io/kubernetes-credentials-provider-plugin/examples/) aqui descritos, asi como como [inyectarlos](https://docs.cloudbees.com/docs/cloudbees-ci/latest/cloud-secure-guide/injecting-secrets) desde Jenkins. Tambien en la [documentacion oficial](https://www.jenkins.io/doc/book/pipeline/syntax/#environment) se puede encontrar buena informacion.

## Para utilizar credenciales almacenadas en un Secret en Openshift
El secreto deben haber sido creado de la siguiente manera:

```yaml
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


