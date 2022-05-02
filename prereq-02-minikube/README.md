# Prerequisite 02 - Minikube

Minikube is a tool that makes it easy to run Kubernetes locally. Minikube runs a single-node Kubernetes cluster inside a VM on your laptop for users looking to try out Kubernetes or develop with it day-to-day.

We will first install `minikube` through `brew`.

## Step 0 - Install `brew`

If you have not yet installed `brew`, install it :

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Step 1: Installing Minikube

The easiest way to install Minikube is by using [homebrew](https://brew.sh/). The following command will install Minikube.

```
brew install minikube
```

To verify that the installation is succesfull we can try to get the version of Minikube with the following command :

```
minikube version

---

minikube version: v1.4.0
commit: 7969c25a98a018b94ea87d949350f3271e9d64b6
```

## Step 2: Running Minikube

To start Minikube run the `minikube start` command (it might take a couple of minutes before Minikube has started):

```
minikube start

---

😄  minikube v1.4.0 on Darwin 10.14.6
👍  Upgrading from Kubernetes 1.14.2 to 1.16.0
💿  Downloading VM boot image ...
    > minikube-v1.4.0.iso.sha256: 65 B / 65 B [--------------] 100.00% ? p/s 0s
    > minikube-v1.4.0.iso: 135.73 MiB / 135.73 MiB [-] 100.00% 17.28 MiB p/s 8s
💡  Tip: Use 'minikube start -p <name>' to create a new cluster, or 'minikube delete' to delete this one.
🔄  Starting existing virtualbox VM for "minikube" ...
⌛  Waiting for the host to be provisioned ...
🐳  Preparing Kubernetes v1.16.0 on Docker 18.09.6 ...
💾  Downloading kubelet v1.16.0
💾  Downloading kubeadm v1.16.0
🚜  Pulling images ...
🔄  Relaunching Kubernetes using kubeadm ...
⌛  Waiting for: apiserver proxy etcd scheduler controller dns
🏄  Done! kubectl is now configured to use "minikube"
```

To verify that minikube is running correctly run the `minikube status` command:

```
minikube status

---

minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

## Step 3: Disable Minikube

If you validated that `minikube` is working, you can stop it until you need in the workshop (as `minikube` runs inside a VM it will use quite a lot of CPU and memory if you leave it running):

```
minikube stop
```