# STARTX helm : cluster-istio

This helm chart is used to configure Istio at the cluster level.
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
helm show chart startx/cluster-istio
```

### 4. Install this chart

```bash
helm install startx/cluster-istio
```

## Default values

Complete deployment of a project with the following characteristics :

xxxx to do xxxxxx

```bash
# base configuration running default configuration
helm install startx/cluster-istio
```

## Others values availables

- **startx** : Startx Istio service configuration using service-mesh operator (see [values-startx.yaml](https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-istio/values-startx.yaml))

```bash
helm install startx/cluster-istio -f https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-istio/values-startx.yaml
```

## History

| Release | Date       | Description
| ------- | ---------- | -----------------------------------------------------
| 0.3.21  | 2020-11-07 | Add ServiceMesh deployment with elastic,kiali and jager dependencies management. Could create a controlPlane and memberroll.
| 0.3.23  | 2020-11-07 | Add engineVersion to all chart (set to 4.5.12) and update all appVersion with the relevant information
| 0.3.29  | 2020-11-07 | Improve NOTES output and move to 0.3.25 dependencies
| 0.3.47  | 2020-11-08 | Update dependency to 0.3.45 release
| 0.3.93  | 2020-11-10 | Move to 0.3.93 dependencies for all cluster-xxx charts in the startx repository
| 0.3.105  | 2020-11-11 | Update cluster-xxx charts dependencies to 0.3.103 release
| 0.3.117  | 2020-11-12 | Move to 0.3.115 basic chart dependencies
| 0.3.126  | 2020-11-14 | Move to a servie mesh usage
| 0.3.135  | 2020-11-15 | Add multiple value (istio member only) and enable ServiceMeshMember only for this chart
| 0.3.135  | 2020-11-23 | Improve documentation for all examples charts
| 0.3.141 | 2020-11-24 | publish stable update for the full repository
| 0.3.151 | 2021-01-23 | Upgrade istio to version 2.0.0.2
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
