# Pod Webhook Example

## Local Development

```sh
kind create cluster

./hack/setup.sh

make kind-deploy IMG=example.com/abc/manager:v0.0.1

# Wait for pods to become ready.
kubectl get pods -n pod-webhook-example-system

# Apply an example Pod.
kubectl apply -f hack/pod.yaml
```
# pod-webhook-example
