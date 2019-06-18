# Restart gcp

shut down vm 

shut down database 

start database 

start vm 

confirm database ip  \(vm-ip\)  
[https://console.cloud.google.com/sql/instances/polling-app-mysql/connections?project=new-project-231716](https://console.cloud.google.com/sql/instances/polling-app-mysql/connections?project=new-project-231716)  
[https://console.cloud.google.com/compute/instances?project=new-project-231716&instancessize=50](https://console.cloud.google.com/compute/instances?project=new-project-231716&instancessize=50)

gcloud auth login

kubectl get pods 

kubectl delete pod polling-backend-646db47759-kt5kb自己會長出來 

kubectl delete pod --all 

kubectl delete pods --all --grace-period=0 --force

