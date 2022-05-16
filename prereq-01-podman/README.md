# Prerequisite 01 - Podman

We will first install `podman` through `brew`.

## Step 0: Install `brew`

If you have not yet installed `brew`, install it :

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Step 1: Install Podman

Install `podman` using the command below:

```
brew install podman
```

Start the Podman-managed VM:

```
podman machine init
podman machine start
```

Ensure that everything is working:

```
podman version

---

Client:       Podman Engine
Version:      4.0.3
API Version:  4.0.3
Go Version:   go1.18
Built:        Fri Apr  1 17:28:59 2022
OS/Arch:      darwin/amd64

Server:       Podman Engine
Version:      4.0.2
API Version:  4.0.2
Go Version:   go1.16.14
Built:        Thu Mar  3 15:56:56 2022
OS/Arch:      linux/amd64
```

## Step 2: Disable Podman

If you validated that `podman` is working, you can stop it until you need in the workshop (as `podman` runs inside a VM it will use quite a lot of CPU and memory if you leave it running):

```
podman machine stop
```
