# nso-replace-testing

Repo to test various scenarios related to the addition of the `__state: replace`
option in nso_config ansible module

## Background

[Ansible Feature Request](https://github.com/ansible/ansible/issues/39278)
[Development Branch](https://github.com/cnasten/ansible/tree/cnasten/devel)


## Setup

```
ncs-netsim create-network cisco-ios 1 router
ncs-netsim start
ncs-setup --dest .
ncs
```
