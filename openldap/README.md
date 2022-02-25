## Pre-requisite:


A docker secret needs to be created to pull images (`osixia/openldap:stable` & `osixia/phpldapadmin:stable`) prior to deploying the openldap NodePort service from the ldap-app.yaml. Refer the command below to create the docker secret

Note 1: The secret name "docker" is referenced inside of the "ldap-app.yaml" file

Note 2: Replace values inside <> with your actual docker account related values

    oc create secret docker-registry docker --docker-username=<docker-username> --docker-password=<docker-token> --docker-email=<email-associated-with-docker-account>

## Creating LDAP deployment and LDAP NodePort service

- Execute `oc create -f ldap-app.yaml` to create LDAP deployment and LDAP NodePort service.

Note: The LDAP deployment will have pre-populated users


## Verifying LDAP deployment and pre-populated users from the CLI

- Execute below command in default namespace to get LDAP pod name

    `oc get pods -n default | grep openldap  `  

- Execute the below command to gain access to the LDAP pod shell;

   `oc exec -it <openldap pod name> -- bash`


- At the pod shell, execute below command to verify users have been added;
(Note: enter the password as adminpassword when prompted for LDAP password)

    `ldapsearch -x -b "dc=alm,dc=com" -D "cn=admin,dc=alm,dc=com" -W`
    
## Verifying OpenLDAP users are pre-populated from the PHPLDAPAdmin GUI

Execute `oc get nodes -o wide` to get IP of one of the Bare Metal nodes

Execute `oc get svc | grep openldap` to get port (30080 in this case) of where the GUI services is available
    
Launch a browser and type the URL `http://<NodeIP>:30080` and type username = `cn=admin,dc=alm,dc=com` and password = `adminpassword`
