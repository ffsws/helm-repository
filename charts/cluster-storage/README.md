# STARTX helm : cluster-storage

This helm chart is used to create a list of storageClass available for the cluster.
This chart is part of the cluster-xxx startx helm chart that doesn't create application deployment but rather represent a cluster configuration state orchestrated by gitops tools like ArgoCD.

## Requirements and guidelines

Read the [startx helm-repository homepage](https://startxfr.github.io/helm-repository) for
more information on how to use theses resources.

## Deploy this helm chart on openshift

### 1. Connect to your Openshift cluster

```bash
oc login -t <token> <cluster-url>
```

### 2. Install the repository

```bash
helm repo add startx https://startxfr.github.io/helm-repository/packages/
```

### 3. Get information about this chart

```bash
helm show chart startx/cluster-storage
```

### 4. Install this chart

```bash
helm install startx/cluster-storage
```

## Default values

Deployment of storage classes :

- 1 **storageClass** named **example-gp2** with the following characteristics
  - **provisioner** set to **kubernetes.io/aws-ebs**
  - provisioner **encryption** specific parameters set to **true**
  - storage class **reclaim policy** set to **Delete**
  - storage class **volume expansion enabled**
  - storage class **volume binding mode** set to **WaitForFirstConsumer**

```bash
# base configuration running default configuration
helm install startx/cluster-storage
```

## Others values availables

- **startx** : Startx storage classes running under AWS infrastructure (see [values.yaml](https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-storage/values-startx.yaml)) creating the following storage classes
  - **aws-generic-retain** (AWS EBS gp2 level with encryption and expansion enabled with retain policy)
  - **aws-generic-delete** (AWS EBS gp2 level with encryption and expansion enabled with delete policy)
  - **aws-fast-retain** (AWS EBS io1 level without encryption and expansion enabled with retain policy)
  - **aws-fast-delete** (AWS EBS io1 level without encryption and expansion enabled with delete policy)
  - **aws-slow-retain** (AWS EBS sc1 level with encryption and expansion enabled with retain policy)
  - **aws-slow-delete** (AWS EBS sc1 level with encryption and expansion enabled with delete policy)

```bash
helm install startx/cluster-storage -f https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-storage/values-startx.yaml
```

- **startx-ocs** : Startx storage classes for OCS infrastructure (see [values.yaml](https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-storage/values-startx-ocs.yaml)) creating the following storage classes
  - **ocs-generic-retain** (OCS provisionned via openshift-storage.rbd.csi.ceph.com in cluster openshift-storage with retain policy and expansion enabled)
  - **ocs-generic-delete** (OCS provisionned via openshift-storage.rbd.csi.ceph.com in cluster openshift-storage with delete policy and expansion enabled)
  - **ocs-fs-retain** (OCS provisionned via openshift-storage.cephfs.csi.ceph.com in cluster openshift-storage with retain policy)
  - **ocs-fs-delete** (OCS provisionned via openshift-storage.cephfs.csi.ceph.com in cluster openshift-storage with delete policy)

```bash
helm install startx/cluster-storage -f https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-storage/values-startx-ocs.yaml
```

## History

| Release | Date       | Description
| ------- | ---------- | -----------------------------------------------------
| 0.2.0   | 2020-10-23 | Initial commit for this helm chart with default value example (removed)
| 0.2.51  | 2020-10-31 | Common release for all chart
| 0.2.93  | 2020-10-31 | Align all startx charts version to 0.2.93. Preparing stable 0.3 release
| 0.3.0   | 2020-10-31 | Stable 0.3 release
| 0.3.21  | 2020-11-06 | Align all charts on the repository release 0.3.21
| 0.3.23  | 2020-11-07 | Add engineVersion to all chart (set to 4.5.12) and update all appVersion with the relevant information
| 0.3.47  | 2020-11-08 | Update dependency to 0.3.45 release
| 0.3.93  | 2020-11-10 | Move to 0.3.93 dependencies for all cluster-xxx charts in the startx repository
| 0.3.105  | 2020-11-11 | Update cluster-xxx charts dependencies to 0.3.103 release
| 0.3.117  | 2020-11-12 | Move to 0.3.115 basic chart dependencies
| 0.3.135  | 2020-11-23 | Improve documentation for all examples charts
| 0.3.141 | 2020-11-24 | publish stable update for the full repository
| 0.3.151 | 2021-01-23 | Upgrade to OCP version 4.6.13
| 0.3.151 | 2021-01-23 | Upgrade chart to OCP version 4.3.13
| 0.3.153 | 2021-01-23 | publish stable update for the full repository
| 0.3.165 | 2021-01-23 | Upgrade all chart dependencies
| 0.3.167 | 2021-01-24 | Remove conditional dependencies for argocd compatibility in HA environments
| 0.3.169 | 2021-01-24 | Move to 0.3.155 dependencies
| 0.3.173 | 2021-01-24 | Move all dependencies to 0.3.171 and improve cluster-logging component
| 0.3.175 | 2021-01-25 | publish stable update for the full repository
| 0.3.176 | 2021-01-25 | publish stable update for the full repository
| 0.3.179 | 2021-01-30 | publish stable update for the full repository
| 0.3.181 | 2021-02-11 | publish stable update for the full repository
| 0.3.183 | 2021-02-12 | Unstable release for all cluster charts
