# execute-remote-pipeline
Tekton task for executing a Tekton pipeline that is located on a remote OpenShift cluster

On the remote OpenShift cluster, you will need to create a service account that will be used for starting the pipeline.

```
$ oc create sa pipeline-starter
```

```
$ oc sa get-token pipeline-starter
```


