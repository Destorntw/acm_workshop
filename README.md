# RHACM Workshop Instructions

## Table of Contents
1. [Explore - Obtain Credentials](#1-explore---obtain-credentials)
2. [Install Red Hat Advanced Cluster Management (RHACM)](#2-install-red-hat-advanced-cluster-management-rhacm)
3. [Provision a New OpenShift Cluster](#3-provision-a-new-openshift-cluster)
4. [Create Policies in a Git Repository](#4-create-policies-in-a-git-repository)
    - [Policy 1: Create a New Cluster Admin User](#policy-1-create-a-new-cluster-admin-user)
    - [Policy 2: Set the Upgrade Channel](#policy-2-set-the-upgrade-channel)
    - [Policy 3: Delete the KubeAdmin User](#policy-3-delete-the-kubeadmin-user)
5. [Apply Policies Using the Governance and Compliance Pane](#5-apply-policies-using-the-governance-and-compliance-pane)
6. [Install, Configure, and Explore the OSUS Operator](#6-install-configure-and-explore-the-osus-operator)
7. [Update the Cluster, Verify, and Cleanup](#7-update-the-cluster-verify-and-cleanup)

---

## 1. Explore - Obtain Credentials
1. Obtain your workshop credentials from the facilitator.
2. Ensure you have access to the OpenShift and RHACM consoles.

> **Documentation Reference:** 
> - [OpenShift Console](https://docs.openshift.com/container-platform/latest/welcome/index.html)

---

## 2. Install Red Hat Advanced Cluster Management (RHACM)
1. Log in to your OpenShift hub cluster.
2. Install the RHACM operator from the OperatorHub.
3. Verify that RHACM is installed by navigating to the RHACM console.

> **Documentation Reference:**
> - [Installing RHACM](https://docs.redhat.com/en/documentation/red_hat_advanced_cluster_management_for_kubernetes/2.11/html/install/index)

---

## 3. Provision a New OpenShift Cluster
1. Use RHACM to provision a new managed OpenShift cluster (v4.16).
2. Follow the prompts to specify cluster settings such as region, size, and credentials.
3. Monitor the cluster provisioning progress in RHACM.

> **Documentation Reference:**
> - [Provisioning Clusters](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/latest/html/clusters/index)

---

## 4. Create Policies in a Git Repository
### 4.1 Policy 1: Create a New Cluster Admin User
1. Write a policy YAML file to create a new cluster admin user with a strong password.

```yaml
apiVersion: policy.open-cluster-management.io/v1
kind: Policy
metadata:
  name: create-cluster-admin
spec:
  remediationAction: enforce
  policy-templates:
    - objectDefinition:
        apiVersion: user.openshift.io/v1
        kind: User
        metadata:
          name: new-cluster-admin
        password: <strong-password>
```

### 4.2 Policy 2: Set the Upgrade Channel
1. Write a policy YAML file to set the upgrade channel for the managed cluster.

```yaml
apiVersion: policy.open-cluster-management.io/v1
kind: Policy
metadata:
  name: set-upgrade-channel
spec:
  remediationAction: enforce
  policy-templates:
    - objectDefinition:
        apiVersion: config.openshift.io/v1
        kind: ClusterVersion
        spec:
          channel: stable-4.16
```

### 4.3 Policy 3: Delete the KubeAdmin User
1. Write a policy YAML file to delete the default KubeAdmin user on the managed cluster.

```yaml
apiVersion: policy.open-cluster-management.io/v1
kind: Policy
metadata:
  name: delete-kubeadmin
spec:
  remediationAction: enforce
  policy-templates:
    - objectDefinition:
        apiVersion: user.openshift.io/v1
        kind: User
        metadata:
          name: kubeadmin
```

> **Documentation Reference:**
> - [Policy Framework](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/latest/html/governance/governance)

---

## 5. Apply Policies Using the Governance and Compliance Pane
1. Navigate to the Governance and Compliance pane in RHACM.
2. Import your Git repository containing the policy YAML files.
3. Apply the policies to the managed cluster.
4. Test the new admin user to ensure it is functional.

> **Documentation Reference:**
> - [Governance and Compliance](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/latest/html/governance/governance)

---

## 6. Install, Configure, and Explore the OSUS Operator
1. Install the OpenShift Update Service (OSUS) operator on the managed cluster.
2. Configure OSUS to manage updates for your cluster.
3. Explore the features provided by the OSUS operator.

> **Documentation Reference:**
> - [OSUS Operator](https://docs.openshift.com/container-platform/latest/updating/osus-operator.html)

---

## 7. Update the Cluster, Verify, and Cleanup
1. Use the OSUS operator to update the cluster to the latest version.
2. Verify that the update was successful.
3. Delete the managed cluster from RHACM to clean up resources.

> **Documentation Reference:**
> - [Cluster Updates](https://docs.openshift.com/container-platform/latest/updating/updating-cluster.html)
- [Deleting Clusters](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/latest/html/clusters/managing-clusters#delete-clusters)
