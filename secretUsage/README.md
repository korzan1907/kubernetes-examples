#################################################################
## Ozan Güzeldereli
##
## Secret Usage Example in Kubernetes
#################################################################

This directory contains the example to:
- Create an SSL Key
-


Commands to follow:

# Before running the secret change www.ozanguzeldereli.com with your prefered address. Run createSecrets.sh which will create the crt and key files
./createSecrets.sh
 
# Create ConfigMaps from folder that will be needed for nginx configuration
kubectl create configmap nginx-config --from-file=configmap-files/my-nginx-config.conf

# Create secret http-secret
kubectl create secret generic https-secret --from-file=https.key --from-file=https.cert


# Expose pod to port 8443
kubectl port-forward $(kubectl get po -l app=secret-example-usage-app -o jsonpath='{.items[*].metadata.name}') 8443:443

# Test the pod to see if its working
curl https://localhost:8443 -k -v
