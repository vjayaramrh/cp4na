This directory contains the YAML files that can be used to install Red Hat Advanced Cluster Management for Kubernetes (RHACM) hub cluster and to create the `MultiClusterHub` custom resource.

## Pre-Requisites:
- Red Hat OpenShift Container Platform cluster must be installed.
- OpenShift Container Platform CLI must be installed.
- No previous installations of RHACM should be present. 


## Steps to install RHACM and its custom instance:
1. Run the command `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/acm/2.4/01-namespace-acm.yaml` to create a custom RHACM hub cluster namespace (which is `open-cluster-management` in the case here).
- The YAMl files that follow have been modified to use the `open-cluster-management` namespace as the namespace to be worked on. 

2. Run the command `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/acm/2.4/02-operator-group-acm.yaml` to create an `OperatorGroup` resource for RHACM.

3. Run the command `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/acm/2.4/03-subscription-acm.yaml` to create and configure a subscription for the RHACM operator.

4. Run the command `oc create -f https://github.com/redhat-eets/cp4na/blob/main/acm/2.4/04-multiclusterhub-instance-acm.yaml` to create and configure the `MultiClusterHub` custom resource.

5. Once the custom resource is installed, run the command `oc get mch -o=jsonpath='{.items[0].status.phase}' -n open-cluster-management` to check the status of the custom resource. It has to display `Running` as the status.

6. To acquire the link to the RHACM hub cluster console, run the command `oc get routes -n open-cluster-management` which would look like `multicloud-console.apps.ocp4ai.oot.lab.eng.bos.redhat.com` for example.

7. Add the link in the `/etc/hosts` file as a hostname/DNS entry with the same IP address mapped to the hosting OCP cluster. Now, the link should be directly accessible.
