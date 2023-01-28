## Deployment of Microservice Application using Helm charts and Helmfile 

The demo app used in this project is forked project from Google Cloud Platformshows a simple user profile app set up using 
- Forked link: https://github.com/shakayhere/kubernetes-microservices-demo
- Original link: https://github.com/GoogleCloudPlatform/microservices-demo

All values.yaml files are created for the mentioned project.

#### Dependencies to Install

- <b>kubectl</b> should be installed to communicate with k8s API. Follow the steps attached in the link: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

- <b>Helm</b> should be installed to run the application. Follow the steps attached in the link: https://helm.sh/docs/intro/install/

- <b>Minikube</b> is used to set up cluster on local machine. Follow the steps in the link to install: https://minikube.sigs.k8s.io/docs/start/

- <b>Helmfile</b> is used to deploy multiple helm charts. Installation link: https://helmfile.readthedocs.io/en/latest/#installation

### Run on your machine with bash script

#### To start the application

Start your kubernetes cluster by using minikube with the following command:

    minikube start

Clone this repository and install all components using by executing the following command in root directory of your repo:

    ./install.sh
    

To access your application, you need to create a tunnel in minikube to give services an external IP that requested one. You can do this by using the dollowing command:

    minikube tunnel

Check your frontend service for external IP. From that, you can access the application in the browser. To check service of frontend, use the following:

    kubectl get svc/frontend

Uninstall all components using the following

    ./uninstall

### Run on your machine with Helmfile

Clone this repository and install all components using by executing the following command in root directory of your repo:

    helmfile sync
    
To access your application, you need to create a tunnel in minikube to give services an external IP that requested one. You can do this by using the dollowing command:

    minikube tunnel

Check your frontend service for external IP. From that, you can access the application in the browser. To check service of frontend, use the following:

    kubectl get svc/frontend

Uninstall all components using the following

    helmfile destroy

### Cleanup

Stop your minikube cluster with the following:

    minikube stop
    
You can also destroy your minikube image and free up some space with:

    minikube delete
