# ceph-csi

安装 rook-ceph，支持 rdb 块存储及 cephfs 文件存储

安装前需要所有机器满足:

<https://rook.io/docs/rook/v1.0/k8s-pre-reqs.html#lvm-package>

## Access dashboard

存在一个 bug，dashboard service 不能 port-forward 尚未解决

此处需要直接从 pod 中 forward 出来

```sh
kubectl -n rook-ceph get svc rook-ceph-mgr-dashboard -o yaml
# find which pod for dashboard, then
kubectl -n rook-ceph port-forward pod/rook-ceph-mgr-b-855f699f68-dm5gf 7000:7000
```

访问 `http://localhost:7000`

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

ceph status
ceph osd status
ceph osd tree
ceph df
rados df
ceph fs ls

pvcs stay in pending state?

<https://rook.github.io/docs/rook/v1.5/ceph-common-issues.html#pvcs-stay-in-pending-state>
