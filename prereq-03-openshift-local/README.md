# Prerequisite 03 - CRC/OpenShift Local

To use OpenShift on our laptop we're going to use CRC (OpenShift Local):

https://github.com/code-ready/crc

CRC is a tool that helps you run OpenShift locally by running a single-node OpenShift cluster inside a VM. You can try out OpenShift or develop with it, day-to-day, on your local host.

### Step 1: Install CRC .pkg package 

Download and install the latest release of CRC:
https://console.redhat.com/openshift/create/local

> NOTE: you will need to create an account on the Red Hat website and install the `.pkg` package by double clicking it

### Step 2: Configure and install OpenShift Local

Go to your terminal and issue the following command to not send any telemetry data back to Red Hat:

```
crc config set consent-telemetry no

---

Successfully configured consent-telemetry to no
```

Now issue the following command to setup your CRC (OpenShift Local) environment:

```
crc setup

---

INFO Using bundle path /Users/trescst/.crc/cache/crc_hyperkit_4.10.9_amd64.crcbundle 
INFO Checking if running as non-root              
INFO Checking if crc-admin-helper executable is cached 
INFO Checking for obsolete admin-helper executable 
INFO Checking if running on a supported CPU architecture 
INFO Checking minimum RAM requirements            
INFO Checking if crc executable symlink exists    
INFO Checking if running emulated on a M1 CPU     
INFO Checking if HyperKit is installed            
INFO Checking if qcow-tool is installed           
INFO Checking if crc-driver-hyperkit is installed 
INFO Checking if CRC bundle is extracted in '$HOME/.crc' 
INFO Checking if /Users/trescst/.crc/cache/crc_hyperkit_4.10.9_amd64.crcbundle exists 
INFO Checking if old launchd config for tray and/or daemon exists 
INFO Checking if crc daemon plist file is present and loaded 
Your system is correctly setup for using CRC. Use 'crc start' to start the instance
```

> NOTE: the above command will need to download some large files, so ensure you are connected to a decent network and keep in mind that it might take some time to complete

Now start your CRC (OpenShift Local) environment:

```
crc start

---

INFO Checking if running as non-root              
INFO Checking if crc-admin-helper executable is cached 
INFO Checking for obsolete admin-helper executable 
INFO Checking if running on a supported CPU architecture 
INFO Checking minimum RAM requirements            
INFO Checking if crc executable symlink exists    
INFO Checking if running emulated on a M1 CPU     
INFO Checking if HyperKit is installed            
INFO Checking if qcow-tool is installed           
INFO Checking if crc-driver-hyperkit is installed 
INFO Checking if old launchd config for tray and/or daemon exists 
INFO Checking if crc daemon plist file is present and loaded 
INFO Loading bundle: crc_hyperkit_4.10.9_amd64... 
INFO Creating CRC VM for OpenShift 4.10.9...      
INFO Generating new SSH Key pair...               
INFO Generating new password for the kubeadmin user 
INFO Starting CRC VM for OpenShift 4.10.9...      
INFO CRC instance is running with IP 127.0.0.1    
INFO CRC VM is running                            
INFO Updating authorized keys...                  
INFO Check internal and public DNS query...       
INFO Check DNS query from host...                 
INFO Verifying validity of the kubelet certificates... 
INFO Starting OpenShift kubelet service           
INFO Waiting for kube-apiserver availability... [takes around 2min] 
INFO Adding user's pull secret to the cluster...  
INFO Updating SSH key to machine config resource... 
INFO Waiting for user's pull secret part of instance disk... 
INFO Changing the password for the kubeadmin user 
INFO Updating cluster ID...                       
INFO Updating root CA cert to admin-kubeconfig-client-ca configmap... 
INFO Starting OpenShift cluster... [waiting for the cluster to stabilize] 
INFO 3 operators are progressing: image-registry, network, openshift-controller-manager 
INFO Operator openshift-controller-manager is progressing 
INFO Operator openshift-controller-manager is progressing 
INFO 2 operators are progressing: authentication, openshift-controller-manager 
INFO Operator authentication is not yet available 
INFO Operator authentication is not yet available 
INFO All operators are available. Ensuring stability... 
INFO Operators are stable (2/3)...                
INFO Operators are stable (3/3)...                
INFO Adding crc-admin and crc-developer contexts to kubeconfig... 
Started the OpenShift cluster.

The server is accessible via web console at:
  https://console-openshift-console.apps-crc.testing

Log in as administrator:
  Username: kubeadmin
  Password: <...redacted...>

Log in as user:
  Username: developer
  Password: developer

Use the 'oc' command line interface:
  $ eval $(crc oc-env)
  $ oc login -u developer https://api.crc.testing:6443
```

> NOTE: the above command will take some time to complete, when finished it will prompt you with the credentials of your environment

### Step 3: Using OpenShift Local

Configure oc (The openshiftconfig binary) on your terminal.

```
eval $(crc oc-env)
```

Now login using `oc` as the `developer` user:

```
oc login -u developer https://api.crc.testing:6443
```

Verify that this works:

```
oc get cm   

---

NAME                       DATA   AGE
kube-root-ca.crt           1      15d
openshift-service-ca.crt   1      15d
```

### Step 4: Disable OpenShift Local

If you validated that OpenShift Local is working, you can stop it until you need in the workshop (as OpenShift Local runs inside a VM it will use quite a lot of CPU and memory if you leave it running):

```
crc stop
```
