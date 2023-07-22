# Ansible config for Kubernetes home lab

Ansible config for my home lab that is set up with three Orange Pi 5. It sets up a Kubernetes cluster using k3s. It is made specifically for my setup, so it will most likely will not match yours, but feel free to modifiy it or use it as reference.

This config will change over time if I ever need to add some functionality or I need it to be more flexible.

## How to use

It is pretty straightforward. First of all, set up your user and password in `group_vars/all.yml` by completing the variables `ansible_user` and `ansible_sudo_pass` 

After that, create your `hosts.ini` with the following structure

```ini
[master]
<user>@<ip>

[nodes]
<user>@<ip>
<user>@<ip>

[k3s_cluster:children]
master
nodes

```

For example:

```ini
[master]
user@192.168.0.1

[nodes]
user@192.168.0.2
user@192.168.0.3

[k3s_cluster:children]
master
nodes

```

Finally, run it with:
`ansible-playboook site.yaml`