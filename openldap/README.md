A docker secret needs to be created to pull images prior to deploying the openldap service from the ldap-app.yaml. Refer the command below to create the docker secret

Note 1: The secret name "docker" is referenced inside of the "ldap-app.yaml" file

Note 2: Replace values inside <> with your actual docker account related values

    oc create secret docker-registry docker --docker-username=<docker-username> --docker-password=<docker-token> --docker-email=<email-associated-with-docker-account>
