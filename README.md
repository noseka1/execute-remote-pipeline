# Execute Remote Pipeline

This Tekton task executes a Tekton pipeline that is located on a remote OpenShift cluster. The task will tail the output of the remote pipeline while the remote pipeline is executing.

On the remote OpenShift cluster, you will need to create a service account that will be used for starting the pipeline:

```
$ oc create sa pipeline-starter
```

Make sure that this service account has sufficient permissions to execute the pipeline. Find an example in this repo that includes a role with minimum premissions required.

Obtain an authentication token for the service account:

```
$ oc sa get-token pipeline-starter
```

On the local OpenShift cluster, create a secret that will hold the token:

```
$ oc create secret generic --from-literal=openshift-token=INSERT_TOKEN_HERE pipeline-starter
```

Use the *execute-remote-pipeline* task in your pipeline to execute the pipeline on the remote cluster, for example:

```
apiVersion: tekton.dev/v1beta1
kind: Pipeline
metadata:
  name: local
  namespace: local-pipeline
spec:
  tasks:
  - name: execute-remote-pipeline
    taskRef:
      kind: Task
      name: execute-remote-pipeline
    params:
    - name: pipeline-name
      value: remote
    - name: pipeline-namespace
      value: remote-pipeline
    - name: openshift-server-url
      value: INSERT_OPENSHIFT_URL_HERE
    - name: openshift-token-secret
      value: pipeline-starter
```
