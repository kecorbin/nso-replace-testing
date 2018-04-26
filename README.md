# nso-replace-testing

Repo to test various scenarios related to the addition of

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


# Issue #1 - Interfaces

## Overview

For some reason it appears that `__state: replace` is causing `no interface X`
to be attempted.  netsims allow this command but real devices + NEDS would produce the following
error during playbook execution.

```
fatal: [agg3]: FAILED! => {"changed": false, "msg": "NSO commit returned JSON-RPC error: {u'data': {u'message': u\"External error in the NED implementation for device agg3: command: no interface Ethernet1/10: \\r\\r\\n                                      ^\\r\\nInvalid range at '^' marker.\"}, u'message': u'Method failed', u'code': -32000, u'type': u'rpc.method.failed', u'internal': u'jsonrpc_tx_commit257'}"}
```


## Steps to reproduce

* Run `ansible-playbook interfaces.yml` - this will run correctly
* Run `ansible-playbook remove-description.yml`

#### Expected behavior

The description is removed from FastEthernet1/0

#### Actual behavior

FastEthernet1/0 no longer appears in the configuration
