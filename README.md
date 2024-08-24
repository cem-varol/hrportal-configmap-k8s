Spring Boot Web Application 
Dockerized locally in minikube with following steps: 

      - eval $(minikube docker-env)
      - check "docker ps" command in current terminal. minukube related containers should be listed.
      - "docker images" also list images related to minikube
      - docker build -t hrportal:latest .
      - minikube cache add hrportal:latest (pushes image local registry of minikube)
      - minikube cache reload (if necessary)
    
Deployed in k8s (minikube cluster). Following yaml file contains both deployment and external service manifest
      
      - kubectl create -f hrportal-deployment.yaml 
# hrportal-configmap-k8s
