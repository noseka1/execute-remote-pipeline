FROM registry.redhat.io/ubi8/ubi

RUN curl --location \
  https://mirror.openshift.com/pub/openshift-v4/clients/ocp/latest/openshift-client-linux.tar.gz | \
  tar xvfz - --directory /usr/local/bin

RUN rpm --install https://github.com/tektoncd/cli/releases/download/v0.9.0/tektoncd-cli-0.9.0_Linux-64bit.rpm
