Infrastructure as Code
Infrastructure provisioning
(Can also deploy applications)

Build, Version, Change infrastructure in a declarative way.

HCL = Hashicorp Configuration Language
(Optional you can use json)

Usual process of deploy an application:
- Provisioning infrastructure (Prepare infrastructure to be able to run the application)
	- Setup servers
	- Install required tools / databases 
- Deploying applications

**Terraform provisions infarstructure**
- Terraform automates the provisioning steps and runs them in the correct order.

Terraform helps you automating continuous changes to the infrastructure

Terraform lets you spin up identical infrastucture e.g.:
- testing-infrastructure 
- staging-infrastructure 
- production-infrastructure
## How does it work
**Core**
- Uses 2 input sources 
	- TF configs (Desired state)
		- what needs to be proviosioned? How should the infrastructure look like?
	- State (Current state):
		- Current state of the infrastructure 
- Terraform compares the states and heals itself if the states differ
**Providers**
- Cloud-providers (IaaS)
- Kubernetes
- Fastly (SaaS)
	Example: 
	1) TF creates Infrastucture on AWS  
	2) Installs K8s
	3) Creates services inside the K8s Cluster
- Over 100 providers

## How to change the config
To change the terraform config you can just edit the config and re-execute it
- Config stays clean and small since the config is written declarative

