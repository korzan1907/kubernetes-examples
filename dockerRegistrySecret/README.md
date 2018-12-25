#################################################################
## Ozan Güzeldereli
##
## Docker registry secret key usage example
#################################################################

This directory contains example to:
- creation of secret for docker hub
- usage of that secret in deployment.yaml file


# Create mydockerhubsecret docker registry secret with below comment
kubectl create secret docker-registry mydockerhubsecret --docker-username=myusername --docker-password=mypassword  --docker-email=my.email@provider.com

# Use the secret in the deployment, pod etc yaml to deploy the private image
kubectl create -f pod.yaml

