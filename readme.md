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


# if you want some info related to your replicaset 
    command : kubect describe replicaset replicasetname

# to get the configuration of the running replicaset 
    command: kubectl edit rs replicasetName 
    - changes made to this file will directly be applied to the running replicaset \


# DEPLOYMENTS : higher level object of K8 which manages the pod automatically.  
    @@ which is mainly used in production to make these operation automated : 
        - pods & replicaset creation/management  
        - updating apps without downtime
        - Rollbacks to previous versions 
        - Scaling 


    without deployments all these are done manually 

- Deployments manages replicasets and replicaset manages the pods 

=> if you want to update something , the deployment will automatically create new pods and gradually deletes all the old pods 


%% to create a deployment everything is same like creating replicaset just have to change kind to Deployment 


To delete a deployment : 
    command : kubectl delete deployment deploymentName
    automatically delete the replicaset created and the pods also 



# to get the rollout history 
kubectl rollout history deployment/name 

# to get the status of rollout 

kubectl rollout status deployment/name 

# NOTE :
=>  deployment "my-deployment" successfully rolled out

means:

✅ New ReplicaSet created
✅ New Pods created
✅ Pods became Running and Ready
✅ Old Pods terminated successfully
✅ Deployment update completed



# if you want to undo to a previous version :   
-- by default previous version automatically 
    kubectl rollback undo deployment/name --to-revision=NumberFromHistory


# if you want to change the desc for a rollout 

    - kubectl annotate deployment/name kubernetes.io/change-cause="message you want"  --overwrite


# services running 
    - if you have worker node ip directly use workerNodeIp:30004 
    - but on minikube use minikube service serviceName --url 
    -  then hit that url 

  