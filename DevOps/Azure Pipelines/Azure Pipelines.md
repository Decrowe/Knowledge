A pipeline consists out of 2 parts
- CI (Continues Integration)
- CD (Continues Deployment / Delivery)

![[Pasted image 20240702110516.png]]

## Basic Terms
Agent
- Installable software which will run a build or deployment job
Artifact
- Collection of files or packages published by a job. Artifacts are made available for tasks, such as distribution or deployment
Build
- Represents one execution of a pipeline. It collects logs associated with running the steps and test results
CI
- Process of building code. Helps catching bugs early to make them more accessible and faster to fix
- Includes: Automated tests, tests, etc..
- Produce Artifacts

CD
- Increases Quality of product by running tests and builds against one or more test and production stages
- CD systems produce artifacts which can include infrastructure and apps. Pipelines consume those to release new versions and fix existing systems.

Deployment target
- Can be: VM, container, web app, or any other service used to host developed application
- Pipeline might deploy app (artifacts) after build and runs tests against multiple deployment targets.

Job
- A build consists of one or more jobs
- Runs mostly on an agent
- Execution boundary of a set of steps

Pipeline
- Defines CI and CD process for your app
- Made of steps called tasks
- Can be thought as a script that describes how to build, test and deploy your app

Stage
- Primary division in a pipeline. E.g.:
	- "Build the App"
	- "Run Integration Tests"
	- "Deploy to user acceptance testing"

Task
 - Building Block of pipeline
	 - Build Pipeline
		 - Build task
		 - Test task
		 - ...
	- Release Pipeline
		- deployment task
		- ...

Task
- Triggers the pipeline
	- Push new changes
	- Time scheduler
	- Upon completing another build