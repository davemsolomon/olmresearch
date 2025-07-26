#Recipe for spinning up operator pod   
  1. install docker
  2. install minikube
  3. install olm
  4. apply the catalogsource
  5. create namespaces
  6. create operator group
  5. apply subscription

#troubleshooting 
- look in installplan for guidance  
- look in the csv for guidance  
- tail logs - kubectl logs --tail 20 -n olm <pod_name>  


#look at research14.txt to see successful creation of minio operator pod  
daveioop      minio-operator-588d69bc4c-8cgwg                                   1/1     Running     0               2m26s
