kubectl get nodes
kubectl get pods
kubectl get deployments 
kubectl get services

kubectl describe pods 
kubectl describe deployments
kubectl describe services

kubectl cluster info
kubectl run (label) --image=(imageName:verisionlabel) --port=(port)
kubectl delete pods (podname)
kubectl apply -f (path-to-deployment.yaml)
kubectl edit deployment (deployment-name)
kubectl get pods -o wide
kubectl apply -f (path-to-service.yaml)
kubectl edit deployment (deployment-name) 

