## Setting up and basic commands of Kubectl 

> [!CAUTION]
> If the following error is occured: \
> **Command 'kubectl' not found, but can be installed with**

- Install via Snap (recommended for Ubuntu)
```
sudo snap install kubectl --classic
```

1. List the nodes 
```
kubectl get nodes
```

2. Create a deployment with an docker image
> kubectl create deployment <DEPLOYMENT_NAME> --image=<DOCKER_IMAGE>
```
kubectl create deployment nginx-deployment --image=nginx
```

3. List the deployments created
```
kubectl get deployment
```

4. List the pods
```
kubectl get pod
```

5. List the replicasets
```
kubectl get replicaset
```

6. Edit a deployment
> kubectl edit deployment <DEPLOYMENT_NAME>
```
kubectl edit deployment nginx-deployment
```

7. Monitor logs of a pod
> kubectl logs <POD_ID>
```
kubectl logs nginx-deployment-78959b95d4-br7tf
```

--- 

### Delete operations

1. Delete a pod
> kubectl delete pod <POD_ID> --grace-period=0 --force
```
kubectl delete pod mong-deployment-5bc5fbdcb7-9k84k --grace-period=0 --force
```

2. Scale down the repleca set to 0
> kubectl scale <REPLICA_SET_ID> --replicas=0
```
kubectl scale deployment mong-deployment-5bc5fbdcb7-qns6v --replicas=0
```

3. Access the bash CMD of a pod
> kubectl exec -it <POD_ID> -- bin/bash
```
kubectl exec -it mong-deployment-5bc5fbdcb7-9k84k -- bin/bash
```
