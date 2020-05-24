## Prerequisites

Prior to launching this stack, you need to have the following system packages installed:

- vagrant
- vagrant-libvirt plugin
- libvirt
- python3
- python3-virtualenv

## Install dependencies

To install required software to 

```bash
virtualenv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Launch VM

```bash
vagrant up
```

Application should be accessible at http://192.168.240.10.

## Access haproxy stats page

```bash
ssh -i .vagrant/machines/ubuntu/libvirt/private_key -L 8081:127.0.0.1:8081 vagrant@192.168.240.10
```

# Future improvements

Here is a list of future enhancements and what could be fixed:

- make Vagrantfile compatible with other providers than libvirt
- make Vagrantfile more customizable in oder to set VM IP address and resources
- do not log haproxy's HEAD requests in nginx