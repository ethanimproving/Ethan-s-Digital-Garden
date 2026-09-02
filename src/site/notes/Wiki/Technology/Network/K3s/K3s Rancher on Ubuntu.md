---
{"dg-publish":true,"permalink":"/wiki/technology/network/k3s/k3s-rancher-on-ubuntu/","dg-note-properties":{}}
---


# Best Practice for Cluster Naming
```
<cluster-name>-<role>-<index>
k3-lab-01
```

# Setup A Record On Namecheap

## NameCheap A Record

Visit [NameCheap](https://ap.www.namecheap.com/Domains/DomainControlPanel/millernest.com/advancedns).

![](https://i.imgur.com/qUqAdY7.png)


## Proxy Manager

Get your node IP

```shell
ip addr show
```

### NGINX Proxy Manager config (THIS is the key)

Create a **Proxy Host** in NGINXProxyManager:

| Setting               | Value                    |
| --------------------- | ------------------------ |
| Domain                | `rancher.millernest.com` |
| Scheme                | **https**                |
| Forward Hostname      | `192.168.1.xxx`          |
| Forward Port          | `31046`                  |
| Websockets            | ✅ ON                     |
| Block Common Exploits | ✅ ON                     |

### Copy Let's Encrypt Cert

# Install K3s

```bash
# Install k3s
curl -sfL https://get.k3s.io | sh -

# Install Helm v3
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Install cert-manager (Rancher requirement)
helm repo add jetstack https://charts.jetstack.io
helm repo update

# Install cert-manager
sudo kubectl create namespace cert-manager
helm install cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --version v1.14.4 \
  --set installCRDs=true
# Verify
sudo kubectl get pods -n cert-manager

# Create Rancher namespace
sudo kubectl create namespace cattle-system

# Install Rancher:
helm install rancher rancher-latest/rancher \
  --namespace cattle-system \
  --set hostname=rancher.millernest.com \
  --set replicas=1 \
  --set ingress.tls.source=letsEncrypt \
  --set letsEncrypt.email=ethan.romans5.8@gmail.com \
  --set letsEncrypt.environment=production

# Wait for Rancher to start
sudo kubectl -n cattle-system rollout status deploy/rancher

# Check pods
sudo kubectl -n cattle-system get pods

# Verify Which Ports Rancher Is Using
sudo kubectl -n cattle-system get svc

# Check the Rancher ingress
sudo kubectl -n cattle-system get ingress

# Quick Validation (Local DNS)
nslookup rancher.millernest.com
curl -k https://rancher.millernest.com

# (Public DNS)
nslookup rancher.millernest.com 8.8.8.8

# Add Local DNS Override (CHANGE TO YOUR IP)
sudo nano /etc/hosts
<192.168.1.xxx> rancher.millernest.com

# Rancher ingress should NOT use cert-manager
sudo kubectl -n cattle-system edit ingress rancher

# Remove
spec:
  tls:

# Change Rancher service to NodePort
sudo kubectl -n cattle-system edit svc rancher
# Change type: ClusterIP → type: NodePort

# Check NodePort assigned
sudo kubectl -n cattle-system get svc rancher

# Get the Rancher bootstrap password
sudo kubectl get secret --namespace cattle-system bootstrap-secret \
  -o go-template='{{.data.bootstrapPassword|base64decode}}{{"\n"}}'
  
```
[^1]
1. Visit https://192.168.1.206:31046/dashboard/auth/login (Use your server IP)
2. Login with the secret copied from the above command. 

# Copy the kubeconfig to your user

1. Copy the k3s kubeconfig to your home directory:
```bash
mkdir -p $HOME/.kube
sudo cp /etc/rancher/k3s/k3s.yaml $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

Now, `kubectl` will use your user’s kubeconfig:

![](https://i.imgur.com/V4AQbde.png)

# Use a proper DNS hostname

Map that hostname to your IP in your /etc/hosts file (or local DNS):
```
sudo nano /etc/hosts
# Add this line:
192.168.1.206  rancher.k3-lab.local

# After this, install Rancher again
helm install rancher rancher-latest/rancher \
  --namespace cattle-system \
  --set hostname=rancher.k3-lab.local \
  --set replicas=1 \
  --set ingress.tls.source=none
```

# Download kubeconfig

![](https://i.imgur.com/iicXhFB.png)

Download OpenLens for the best Rancher IDE out there, and import the `kubeconfig` as follows:
![](https://i.imgur.com/Ikp2rza.png)

Add `insecure-skip-tls-verify: true` to ignore TLS validation (fastest for lab).
```yaml
clusters:
- name: "local"
  cluster:
    server: "https://192.168.1.206:31046/k8s/clusters/local"
    insecure-skip-tls-verify: true
```


---
[^1]: [Rancher 1.6 Docs](https://www.rancher.com/docs/rancher/v1.6/en/installing-rancher/installing-server/)