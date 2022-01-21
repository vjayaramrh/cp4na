As a first step and prior to deploying openldap using the ldap-app.yaml, create a docker secret named "docker" in the default project space which is needed later for deploying OpenLDAP service by executing the below command.

Note 1: The secret name "docker" is referred inside of the "ldap-app.yaml" file

Note 2: Replace values inside <> with your actual docker account related values

    oc create secret docker-registry docker --docker-username=<docker-username> --docker-password=<docker-token> --docker-email=<email-associated-with-docker-account>
