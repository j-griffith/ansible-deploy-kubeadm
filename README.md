# kube-cluster - use ansible to setup/deploy kubeadm as well as kvm on a nodes

Basic ansible playbooks to setup KVM and deploy kubeadm, after running these playbooks you should have a function kubernetes deployment that supports running kubevirt.

## assign-hostnames

This gives us the ability to fix up VMs that used a template or qcow file and all have the same hostname.  Used the ansible_hostname specified for the ip address in the hosts.ini file.  Changes the hostname, sets up `/etc/hosts` and does a reboot.

## kube-dependencies

Should be run on all hosts, installs kubeadm and all of it's dependencies as well as kvm and sets up nested virt.  Basically everything is ready to go at this point and you can just run the deployment playbooks to perform kubadm init.

## master

Sets up the master node with flannel and the default pod network.

## workers

Sets up the worker nodes, reaches out to the master to get the appropriate join command.
