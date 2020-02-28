
Modified from [shamil/docker-jenkins-auto-slave](https://github.com/shamil/docker-jenkins-auto-slave)

**Auto-trigger Docker Hub's build when new tag (numeric + dots) is applied**

## Jenkins auto slave

* Current image: [oneoneonepig/docker-jenkins-auto-slave:1.0.0](https://hub.docker.com/r/oneoneonepig/docker-jenkins-auto-slave)
* A docker image of Jenkins `JNLP` based agent.
* This image can self-register to Jenkins master
* It will also unregister from the master when container exits.
* `agent.jar` downloaded from Jenkins master when the container starts (avoids versioning problem)

***

## Environment variables

most used variables:
- `JENKINS_AUTH` jenkins server username and either password or API token (in `user:secet` format)
- `JENKINS_URL` jenkins master url (example `http://localhost:8080`)
- `JENKINS_SLAVE_LABEL` space delimited labels, used to group agents into one logical group (no default)
- `JENKINS_SLAVE_MODE` how Jenkins schedules builds on this node, `NORMAL/EXCLUSIVE` (default is `NORMAL`)
- `JENKINS_SLAVE_NAME` the name which will be used when registering (default is `$HOSTNAME`)
- `JENKINS_SLAVE_NUM_EXECUTORS` number of executors to use (defaults to `1`)
- `JAVA_OPTS` pass java options to the `slave.jar` process (default is not set)

## Deployment

```
kubectl apply -f jenkins-master.yaml
kubectl apply -f jenkins-master.yaml
```

## TODO
- [ ] Same service type for http UI and master jnlp listener, expose as NodePort together, which is unnecessary
- [ ] Add username and password option during deployment
- [ ] Pre-install plugins during deployment (or during container packaging)
