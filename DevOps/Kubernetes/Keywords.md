**Master**
- Manages the cluster
- Kubernetes API
- Scheduler
- Controller Manager
- ETCD
**CubeCTL**
- CLI tool to interact with the Kubernetes API
**Cubelet**
- Service running on a node
**CubeProxy**
- 
**Worker Node** 
- A machine on which the pods are running on
- 1 Node can run X pods
**Manifests**
- **Deployment**
	- describe what we want to have
	- like name, label, replicas, imagename, port,...
- **Service**
	- Load balances
	- Exposes pods 
	- describes: names type of serive, port, pod-port
	- defines pods to be load balanced by pod-label! (called selektor)
**Loadbalancer**
- balances the load onto different nodes to keep the individual laod low 
**Pod**
- Container for containers
- Usually one pod holds one container
**Node-Port**
- 1:1 ratio between ips inside and outside the kubernetes cluster