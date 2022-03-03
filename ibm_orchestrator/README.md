This directory contains the yaml files to deploy the IBM CP4NA operator and to create an instance of the operator


Steps to create orchestration instance

1. `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/ibm_orchestrator/01-namespace-ibmcp4na.yaml`

2. `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/ibm_orchestrator/02-ldap-secret.yaml`

3. Execute the command specified in the https://github.com/redhat-eets/cp4na/blob/main/ibm_orchestrator/03-ibm-entitlement-key file. 

4. `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/ibm_orchestrator/04-entitlement-service-account.yaml`

5. `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/ibm_orchestrator/05-ibm-catalog-sources.yaml`

6. `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/ibm_orchestrator/06-ibm-operator-group.yaml`

7. `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/ibm_orchestrator/07-ibm-subscription.yaml`

8. `oc create -f https://raw.githubusercontent.com/redhat-eets/cp4na/main/ibm_orchestrator/08-orchestration-instance.yaml`

9. Edit the orchestration subscription to set the `spec.installPlanApproval` to be `Manual`. Refer https://github.com/redhat-eets/cp4na/blob/main/ibm_orchestrator/09-edit-orchestration-subscription for the command
