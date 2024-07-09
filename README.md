# Impending Kubernetes
## This k8s cluster (using minikube) allows to reference [Synergy chat microservice application](https://github.com/bootdotdev/synergychat/tree/main#crawler-services)
In order to run this cluster do the following:
- Make sure docker and minikube are installed on your system
- Start the minikube cluster and apply all .yaml files to the cluster
- Run `$ minikube tunnel -c` and find out to what IP minikube tunnels the traffic: `route: 10.96.0.0/12 -> EXTERNAL_IP`, you can stop the tunnelling after that
- Edit your DNS configuration so that `synchat.internal` and `synchatapi.internal` corresponse to `EXTERNAL_IP` (edit /etc/hosts in Debian's case)
- Run `$ minikube tunnel -c` and go to `http://synchat.internal` (accessible) and `http://synchatapi.internal` (404 by default by /healthz endpoint should return 200) 
