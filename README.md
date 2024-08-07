# Spacelift Operator

This repository implements a Kubernetes Operator for managing Spacelift resources in a Kubernetes cluster.

## Description

The Controller is responsible for creating and updating resources in Spacelift based on custom resource definitions (CRD). The following resources are supported:

- Stacks
- Runs
- Spaces
- Contexts
- Policies

Note: Currently we do not delete resources in Spacelift when the corresponding custom resource is deleted.

## Installing

```sh
kubectl apply -f https://downloads.spacelift.io/spacelift-operator/latest/manifests.yaml
```

### Create the `spacelift-credentials` secret

To authenticate with the Spacelift API, you need to have an [API Key](https://docs.spacelift.io/integrations/api#spacelift-api-key-token) created in Spacelift.

After that, you need to create a secret in your Kubernetes cluster called `spacelift-credentials` with the following keys:

- `SPACELIFT_API_KEY_ENDPOINT` - the endpoint of the Spacelift API (`https://<account-name>.app.spacelift.io`)
- `SPACELIFT_API_KEY_ID` - the ID of the API key
- `SPACELIFT_API_KEY_SECRET` - the secret of the API key

An example of how to create the secret:

```sh
kubectl create secret generic spacelift-credentials --from-literal=SPACELIFT_API_KEY_ENDPOINT='https://mycorp.app.spacelift.io' --from-literal=SPACELIFT_API_KEY_ID='API_KEY_ID' --from-literal=SPACELIFT_API_KEY_SECRET='API_KEY_SECRET'
```
