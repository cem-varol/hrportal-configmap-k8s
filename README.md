Spring Boot Web Application with ConfigMaps

application.properties file is the common config file for Spring Booot. In this repo you can find how to utilize this file in k8s pods.

TWO APPROACH: 
1) - use direcly configmap in deployment manifest.
   - create a config map with the command
      kubectl create configmap hrportal-app-configmap --from-literal=server.name="PRODSERVER"
   - use this cm as ENV variable in pod.
   - see hrportal-deployment-cm.yaml manifest   
2) - Mount a volume to pod(literally container) that contains application.properties file inside the container.
   - create a config map with file(application.properties) input
      kubectl create configmap hrportal-volume-configmap --from-file=src/main/resources/application.properties
   - Configure volume, volumeMount, and CM in deployment manifest.
   - -See hrportal-deployment-cm-volume.yaml
In second method value stored in application.properties file (server.name) was read by spring boot app and written into console after the first request. 
(http://pod_ip:nodePort)
