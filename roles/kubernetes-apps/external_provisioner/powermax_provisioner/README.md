CSI PowerMAX Volume Provisioner for Kubernetes 1.13+
====================================================

PowerMAX provisionner is based on a CSI Driver.

To install the provider please make sure to set `helm_enabled: true` in `inventory/mycluster/group_vars/addons.yml` and the following CSI flags in `inventory/mycluster/group_vars/k8s-cluster/k8s-cluster.yml`

```
kube_kubeadm_apiserver_extra_args:
  feature-gates: "VolumeSnapshotDataSource=true,KubeletPluginsWatcher=true,CSINodeInfo=true,CSIDriverRegistry=true,BlockVolume=true,CSIBlockVolume=true"
kube_kubeadm_controller_extra_args:
  feature-gates: "VolumeSnapshotDataSource=true,KubeletPluginsWatcher=true,CSINodeInfo=true,CSIDriverRegistry=true,BlockVolume=true,CSIBlockVolume=true"
kube_kubeadm_scheduler_extra_args:
  feature-gates: "VolumeSnapshotDataSource=true,KubeletPluginsWatcher=true,CSINodeInfo=true,CSIDriverRegistry=true,BlockVolume=true,CSIBlockVolume=true"

kube_feature_gates: ["VolumeSnapshotDataSource=true", "KubeletPluginsWatcher=true", "CSINodeInfo=true", "CSIDriverRegistry=true", "BlockVolume=true", "CSIBlockVolume=true"]

docker_insecure_registries:
  - "k8s.gcr.io"
  - "gcr.io"
  - "quay.io"
```
