# ceph-csi

安装 rook-ceph，支持 rdb 块存储及 cephfs 文件存储

安装前需要所有机器满足:

<https://rook.io/docs/rook/v1.0/k8s-pre-reqs.html#lvm-package>

# Access dashboard

usrename: admin

```
kubectl -n rook-ceph get ingress
kubectl -n rook-ceph get secret rook-ceph-dashboard-password -o jsonpath="{['data']['password']}" | base64 --decode && echo
```

## Requirements

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

## Role Variables

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

## Develop guide

Link to local installed role for convenience.

```
rm -rf /Users/zzs/.ansible/roles/36node.ceph-csi
ln -s $PWD /Users/zzs/.ansible/roles/36node.ceph-csi
```

## Troubleshooting guide

Debug

```sh
kubectl -n rook-ceph exec -it deploy/rook-ceph-tools -- bash
```

ceph status
ceph osd status
ceph df
rados df
ceph fs ls

pvcs stay in pending state?

<https://rook.github.io/docs/rook/v1.5/ceph-common-issues.html#pvcs-stay-in-pending-state>

## License

BSD

## Author Information

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
