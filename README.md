# Pod Webhook Example

## Local Development

```sh
# Create a local cluster.
kind create cluster

# Setup cluster dependencies (cert-manager).
./hack/setup.sh

make kind-deploy IMG=example.com/abc/manager:v0.0.1

# Wait for pods to become ready.
kubectl get pods -n pod-webhook-example-system

# Apply an example Pod.
kubectl apply -f hack/pod.yaml

# ... Edit Pod according to output.
# ... Reapply Pod.

# View mutated Pod.
kubectl get -f ./hack/pod.yaml -oyaml
```
