# Admission Controller Webhooks Setup

This is an example of setting up a ValidatingWebhookConfiguration using a locally (ie same k8s-cluster) hosted webhook server. It will create a fully functional admission-controller that validates `namespaces` and `pods` using the [namespace/label checking api](https://github.com/isaaguilar/admissions-webhook-flask-server/blob/master/app/validating_apis/namespaces.py#L5) and the [pod/probe checking api](https://github.com/isaaguilar/admissions-webhook-flask-server/blob/master/app/validating_apis/pods.py#L5) respectively. 

## Setup

Running `./setup.sh` which will create the following resources in your cluster: 

1. The TLS secret for the server, `admissions-webhook-tls` in the `admissions` namespace.
2. The `admissions-webhook` deployment & service in the `admissions` namespace.
3. Two validating webhook configurations; `pods` and `namespaces`.

## Requirements

- `docker`
- `envsubst` (on OSX can be installed with `brew install gettext`)