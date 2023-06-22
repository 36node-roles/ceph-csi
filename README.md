# ceph-csi

安装 rook-ceph，支持 rdb 块存储及 cephfs 文件存储

安装前需要所有机器满足:

<https://rook.io/docs/rook/v1.0/k8s-pre-reqs.html#lvm-package>

## Access dashboard

访问 `https://ceph.{{ domain }}`

usrename: admin

find password

```sh
kubectl -n rook-ceph get secret rook-ceph-dashboard-password -o jsonpath="{['data']['password']}" | base64 --decode && echo
```

## Develop guide

Link to local installed role for convenience.

```sh
rm -rf /Users/zzs/.ansible/roles/36node.ceph-csi
ln -s $PWD /Users/zzs/.ansible/roles/36node.ceph-csi
```

## Troubleshooting guide

Debug

```sh
kubectl -n rook-ceph exec -it deploy/rook-ceph-tools -- bash
```
查看磁盘格式

lsblk -f

ceph status
ceph osd status
ceph osd tree
ceph df
rados df
ceph fs ls

pvcs stay in pending state?

<https://rook.github.io/docs/rook/v1.5/ceph-common-issues.html#pvcs-stay-in-pending-state>
