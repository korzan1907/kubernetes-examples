#################################################################
## Ozan Güzeldereli
##
## Exposing metadata 
#################################################################

This directory contains the example to:
- Expose the metadata as file in the container
- Expose the metadata as env parameter in the container

The Downward API enables you to expose the pod’s own metadata to the processes running inside that pod.
• The pod’s name
• The pod’s IP address
• The namespace the pod belongs to
• The name of the node the pod is running on
• The name of the service account the pod is running under
• The CPU and memory requests for each container
• The CPU and memory limits for each container
• The pod’s labels
• The pod’s annotations



Commands to follow:

For exposing metadata as env parameter in the container 

# Create the pod with pod-metadata-env.yaml
kubectl apply -f pod-metadata-env.yaml

# Check if the env parameters are set in the container
kubectl exec downward env



For exposing metadata as file in the container "Labels and annotations cannot be exposed through ENV parameters" 

# Create the pod with pod-metadata-file.yaml
kubectl apply -f pod-metadata-file.yaml

# Check if the files are created under /etc/downward
kubectl exec downward-file ls /etc/downward

# Check the files 
kubectl exec downward-file cat /etc/downward/annotations
