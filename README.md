# Impending Kubernetes
### This k8s cluster (using minikube) allows to reference [Synergy chat microservice application](https://github.com/bootdotdev/synergychat/tree/main#crawler-services)
In order to run this cluster do the following:
- Clone this repository (`$ git clone https://github.com/chrxn1c/impending_k8s.git && cd impending_k8s`
- Make sure docker and minikube are installed on your system ([docker_docs](https://docs.docker.com/engine/install/) [minikube_docs](https://minikube.sigs.k8s.io/docs/start/))
- Start the minikube cluster and apply all .yaml files to the cluster: `$ minikube start && kubectl apply -f .`
- Run `$ minikube tunnel -c` and find out to what IP minikube tunnels the traffic: looking for `route: 10.96.0.0/12 -> EXTERNAL_IP` in the output, you can stop the tunnelling after that
- Edit your DNS configuration so that `synchat.internal` and `synchatapi.internal` corresponse to `EXTERNAL_IP` (edit /etc/hosts in Debian's case)
- Run `$ minikube tunnel -c` and go to `http://synchat.internal` (accessible) and `http://synchatapi.internal` (404 by default by /healthz endpoint should return 200) 
