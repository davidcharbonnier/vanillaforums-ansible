# VanillaForums Ansible

## Prerequisites

Prior to launching this stack, you need to have the following system packages installed:

- vagrant
- vagrant-libvirt plugin
- libvirt
- python3
- python3-virtualenv

## Install dependencies

To install required dependencies, issue the following commands:

```bash
virtualenv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Launch VM

In order to launch the virtual machine and its provisionning using Ansible, issue the following command:

```bash
vagrant up
```

Application should be accessible at http://192.168.240.10.

## Access haproxy stats page

As the stat page is only accessible from within the virtual machine itself (listening on localhost), you need to issue an SSH port forwarding command:

```bash
ssh -i .vagrant/machines/ubuntu/libvirt/private_key -L 9000:127.0.0.1:9000 vagrant@192.168.240.10
```

Then, stats page is available at http://127.0.0.1:9000/stats.

## Manually launch Ansible playbook

If required, Ansible playbook can be ran without the `vagrant provision` command, issue these:

```bash
ansible-playbook -i inventory site.yml
```

## Known issues / improvements

Here is a list of future enhancements and what could be fixed:

- make Vagrantfile compatible with other providers than `libvirt`
- make Vagrantfile more customizable in oder to set VM IP address and resources
- do not log Haproxy's HEAD requests in Nginx