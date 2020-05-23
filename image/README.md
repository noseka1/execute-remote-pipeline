# Container image

This container image is suitable for running the *execute-remote-pipeline* task.

Build the image:

```
$ podman build --tag quay.io/noseka1/execute-remote-pipeline:latest .
```

Upload the image to registry:

```
$ podman push quay.io/noseka1/execute-remote-pipeline:latest
```
