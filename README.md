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
7. [Explore cluster and ACM resources, Verify, and Cleanup](#7-explore-cluster-and-acm-resources-verify-and-cleanup)
8. [Bonus exercise](bonus_exercise)


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
1. Create a new Git repository and organize it to hold the policy YAML files.
2. Write three policies as follows:
    - A policy to create a new cluster admin user with a strong password.
    - A policy to set the upgrade channel for the managed cluster.
    - A policy to delete the default KubeAdmin user on the managed cluster.

> **Documentation Reference:**
> - [Policy Framework](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/latest/html/governance/governance)
> - [Using GitOps for Policies](https://docs.redhat.com/en/documentation/red_hat_advanced_cluster_management_for_kubernetes/2.11/html/applications/index)

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
> - [OSUS updating a cluster in disconnected](https://docs.openshift.com/container-platform/4.13/updating/updating-restricted-network-cluster/restricted-network-update-osus.html)
> - [Medium Article: OpenShift Update Service](https://medium.com/@hillayamir/openshift-update-service-your-personal-over-the-air-update-service-776b43230011)

---

## 7. Explore cluster and ACM resources, Verify, and Cleanup
1. Explore managed cluster Namespace on Hub cluster.
2. Explore agent Namespace on managed cluster.
3. Explore RHACM search capabilites.
4. Explore RHACM cluster identifiying objects.
5. Explore clusterlet addons
6. Delete the managed cluster from RHACM to clean up resources. *Please click destroy cluster*

> **Documentation Reference:**
> - [klusterlet addons](https://docs.redhat.com/en/documentation/red_hat_advanced_cluster_management_for_kubernetes/2.11/html/klusterlet_add-ons/index)
> - [Cluster Updates](https://docs.openshift.com/container-platform/4.17/updating/understanding_updates/intro-to-updates.html)
> - [Deleting Clusters](https://docs.redhat.com/en/documentation/red_hat_advanced_cluster_management_for_kubernetes/2.11/html/clusters/cluster_mce_overview#remove-managed-cluster)

---

## 8. Bonus exercise
1. Follow the documentation and install Kyverno using ACM policies and application lifecycle.
* Please note - all resources are planned for RHACM 2.9 please update them in your git (fork original git repo)


> **Documentation Reference:**
> - [kyverno excercise](https://drive.google.com/file/d/1aZSzahI5CYV-ZBjgkr-zxx0jmyiB5RPA/view?usp=sharing)

