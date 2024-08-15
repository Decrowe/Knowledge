Container automation
Container orchestration
Orchestration tool for Pods / Containers

## Uptime
One of **Kubernetes** biggest strengths is keeping application up on running by leveraging the self healing and therewith Holds the Uptime high. 

## Selfhealing
- 2 states: 
	- desired state
	- current state
- Kubernetes allways tries to reach the desired state like it is described in the manifests
- If the current state differ from the desired state kubernetes tries to heal itself
- Examples:
	- A pod is not available anymore
	- The deployment specs changed
	- The Image changed
	- -> Cubernetes will boot up the required pods by itself