# STARTX helm : cluster-3scale

This helm chart is used to create a deployment of a 3scale, operator based, deployment of 3Scale API management tools.
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
helm show chart startx/cluster-3scale
```

### 4. Install this chart

```bash
helm install startx/cluster-3scale
```

## Default values

Complete deployment of a project with the following characteristics :

- 1 **project:** named **startx-3scale** with the following properties
  - 1 **LimitRange:** defined for this projet
  - 1 **Quotas:** defined for this projet
  - 3 **RBAC:** allowing **mygroup_example** to **edit** resources
- 1 **operator:** named **3scale-operator** configured with
  - The **threescale-2.9** channel
  - The **0.6.0** version
  - Deployed under the **openshift-operators** project
  - The **manager** deployed
- 1 **Secret:** named **startx-3scale-rhn** that hold rhn credentials used fo image pulling

```bash
# base configuration running default configuration
helm install startx/cluster-3scale
```

## Others values availables

### Default values


- **startx** : Startx 3scale cluster wide service configuration using startx group (dev, devops and ops) (see [values.yaml](https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-3scale/values-startx.yaml))

```bash
helm install startx/cluster-3scale -f https://raw.githubusercontent.com/startxfr/helm-repository/master/charts/cluster-3scale/values-startx.yaml
```

## History

| Release | Date       | Description
| ------- | ---------- | -----------------------------------------------------
| 0.2.0   | 2020-10-24 | Initial commit for this helm chart with default value example
| 0.2.51  | 2020-10-31 | Common release for all chart
| 0.3.0   | 2020-10-31 | Stable 0.3 release
| 0.3.5   | 2020-11-01 | Update dependency to 0.3.3 release and improve Note display
| 0.3.21  | 2020-11-06 | Align all charts on the repository release 0.3.21
| 0.3.23  | 2020-11-07 | Add engineVersion to all chart (set to 4.5.12) and update all appVersion with the relevant information
| 0.3.33  | 2020-11-07 | publish stable update for the full repository
| 0.3.37  | 2020-11-07 | Improve helm hook ordering cordinated with dependencies
| 0.3.47  | 2020-11-08 | Update dependency to 0.3.45 release
| 0.3.93  | 2020-11-10 | Move to 0.3.93 dependencies for all cluster-xxx charts in the startx repository
| 0.3.105  | 2020-11-11 | Update cluster-xxx charts dependencies to 0.3.103 release
| 0.3.117  | 2020-11-12 | Move to 0.3.115 basic chart dependencies
| 0.3.135  | 2020-11-23 | Improve documentation for all examples charts
| 0.3.141 | 2020-11-24 | publish stable update for the full repository
| 0.3.151 | 2021-01-23 | Upgrade to 3Scale version 0.6.1
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
