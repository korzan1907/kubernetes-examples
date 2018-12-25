#################################################################
##
##
## Ozan Güzeldereli
##
## Attaching ConfigMap as a volume
##
#################################################################

This directory contains examples to :
- Create a ConfigMap from 2 files
- Creates a deployment with one pod
- Attaching this configMap to a pod as volume
- Using values in Configmap as arguments for the comment

Commands to follow:

# Creates a configmap from the folder directory
kubectl create configmap fortune-config --from-file=configmap-files

# Creates the deployment with the pods assigning the configmap as volume
kubectl apply -f deployment.yaml

# Expose pod to port 8000
kubectl port-forward $(kubectl get po -l app=configmap-vol-example -o jsonpath='{.items[*].metadata.name}') 8000:80

# Test the pod to see if its working
curl -H "Accept-Encoding: gzip" -I localhost:8000

# You can check the files through below command 
kubectl exec $(kubectl get po -l app=configmap-vol-example -o jsonpath='{.items[*].metadata.name}') ls /etc/nginx/conf.d
