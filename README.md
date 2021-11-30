# Pod Webhook Example

An example of a [kubebuilder](https://github.com/kubernetes-sigs/kubebuilder) project that implements mutating and validating webhooks for a core type (Pods). NOTE: The kubebuilder tool has native support for implementing webhooks for custom resources.

## Local Quickstart

```sh
# Create a local cluster.
kind create cluster

# Setup cluster dependencies (cert-manager).
./hack/setup.sh

# Deploy to internal cluster (with a placeholder image that is loaded into kind).
make kind-deploy IMG=example.com/abc/manager:v0.0.1

# Wait for Pods to become ready.
kubectl get pods -n pod-webhook-example-system -w

# Apply an example Pod.
kubectl apply -f hack/pod.yaml

# ... Edit Pod according to output, and re-apply ...

# View mutated Pod.
kubectl get -f ./hack/pod.yaml -oyaml | grep injected-annotation
```
