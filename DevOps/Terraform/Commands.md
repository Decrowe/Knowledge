Different stages
**refresh**
- query infrastucture provider to get current state
**plan**
- creates an execution plan
- just a preview no changes to real resources
**apply**
- execute plan
**destroy**
- destroyes all resources / infrastructure created by terraform

**apply** & **destroy** uses **refresh** + **plan** internally