# K8s

A guide to installing and building a Kubernetes cluster using k3d

## k3d

k3d is a lightweight wrapper to run  Lightweight Kubernetes (Rancher Lab’s minimal Kubernetes distribution) in docker. Where you have a cluster with a single node in the form of a master node and a worker node.

[More about k3d](https://k3d.io/v5.6.0/)

### Installation

```bas
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

## kubectl

kubectl command line tool to interact with the Kubernetes cluster control plane using the Kubernetes API.

[More about kubectl](https://kubernetes.io/docs/home/)

### Install kubectl binary with curl on Linux

Download the latest release with the command:

```bash
 curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

Download the kubectl checksum file:

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
```

Validate the kubectl binary against the checksum file:

If valid, the output is:

```console
kubectl: OK
```

If the check fails, `sha256` exits with nonzero status and prints output similar to:

```console
kubectl: FAILED
sha256sum: WARNING: 1 computed checksum did NOT match
```

Install kubectl

```bash
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

**Note:**If you do not have root access on the target system, you can still install kubectl to the `~/.local/bin` directory:

```bash
chmod +x kubectl
mkdir -p ~/.local/bin
mv ./kubectl ~/.local/bin/kubectl
# and then append (or prepend) ~/.local/bin to $PATH
```

Test to ensure the version you installed is up-to-date:

```bash
kubectl version --client
```

### Quick Start

Create a cluster named ```testcluster``` with a single node

```bash
k3d cluster create  testcluster
```

Check cluster nodes

```bash
kubectl get nodes
```

Commad to delete ``testcluster``cluster

```bash
k3d cluster delete testcluster
```
