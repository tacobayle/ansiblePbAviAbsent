# aviGcp

## Goals
Destroy Avi Objects (vs, vsvip, pool, se, segroup, cloud)

## Prerequisites:
1. Make sure ansible is installed
2. Make sure avisdk is installed:
```
pip install avisdk
ansible-galaxy install -f avinetworks.avisdk
```
3. Make sure your ansible host can reach your Avi controller

## Environment:

Terraform tf and Playbook(s) has/have been tested against:

### Ansible

```
avi@ansible:~/ansible/aviLscCloud$ ansible --version
ansible 2.9.5
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/avi/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /home/avi/.local/lib/python2.7/site-packages/ansible
  executable location = /home/avi/.local/bin/ansible
  python version = 2.7.12 (default, Oct  8 2019, 14:14:10) [GCC 5.4.0 20160609]
avi@ansible:~/ansible/aviLscCloud$
```

### Avi version

```
Avi 20.1.1
avisdk 18.2.9
```

### Avi environment

europe-north1

## Input/Parameters:

- Make sure vars/creds.json is defined properly
```
{"avi_credentials": {"username": "admin", "controller": "172.16.1.5", "password": "Avi_2019", "api_version": "17.2.14"}, "avi_cluster": false}
```

## Use the the ansible playbook to:
- delete all the gslbservices
- delete all the vs
- delete all the vsvip
- delete all the pools
- delete all the se
- delete all the segroup (except Default-Group)
- delete the cloud name defined as avi_cloud.name

## Run the playbook:
```
```

### future devlopment:
