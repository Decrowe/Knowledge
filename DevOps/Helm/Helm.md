By parameterizing variables in the manifests in Kubernetes you make it easier to manage, update and understand your packages for you and your team.  

Consists of 2 particular components:
- Configuration (Values.yaml in Kubernetes e.g.)
- Template (in Helm: **Chart**)

## Purpose
Example: Given is a tech-stack consisting of 
- deployment.YAML
- service.YAML
In a small business its easy to handle the manifests.
With growing complexities it will happen more likely that the amount and complexity of the manifests raises. In that case **Helm** helps you out.

Helm takes values defined in a configuration (like a Values.YAML in kubernetes) and makes them accessable inside your manifests.

Values.YAML (Chart)
``` yaml
deployment:
	image: node/mongo
	replicas: 2
```

Before
``` yaml
image: node/mongo
replicas: 2
```

After 
``` yaml
image: {{Values.deployment.image}}
replicas: {{Values.deployment.replicas}}
```


**Chart**
A chart is a template with values defined (YAML)

## Tiller
Service sided component of **Helm**
- takes command sent by the **Helm** client and turns it into something the Kubernetes Cluster can understand