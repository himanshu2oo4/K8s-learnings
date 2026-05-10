# to create/ run a pod yaml file 
    - kuebctl apply -f filename.yaml
# to execute a pod : 
    - kubectl port-forward nginx-pod 80:80 


# Replication Controllers: to maintain the specific no of pods 
- to create the pods from a rc file 
- command : kubectl create -f filename.yaml 

# to delete all the pods created by the rc : 
    run : kubectl delete rc RcName 
        # RcName : setted by your configuration file -> check in metadata


# if you want to scale up or down you can use 
command: kubectl scale --replicas=6 -f .\replication_controller.yaml

