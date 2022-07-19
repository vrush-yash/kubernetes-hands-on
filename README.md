# kubernetes-hands-on

As of now, following simple example is added to the repo:
1. With mariaDB/mysql as DB in backend with tomcat as frontend to read some data from the DB
2. Sample dockerfiles are provided to create docker images locally
    a. How to create images as use with docker-compose, follow here: https://github.com/vrush-yash/docker-hands-on/tree/master/docker-compose
3. Sample kubernetes sample manifest files are provided to deploy the same docker containers on kubernetes.
4. Deploy tomcat and mysql:
  a. Go to a folder above <tomcat-folder-containing-manifest-files>
  b. kubectl apply -k tomcat/
  c. Go to a folder above <mysql-folder-containing-manifest-files>
  d. kubectl apply -k mysql/
5. kubectl get deploy -- to get list of deployments created above, use describe command to get details
6. kubectl get svc -- get list of services with external ip address mapped to tomcat service
7. open browser and open link: http://localhost/jdbctest.jsp

Note: Provided sample manifest files are tested on minikube k8s but should work in similar fasion on k8s installed via kubeadm. In case of any cloud provided k8s, you will need to add the images to container registry of the cloud.

Assuming using OS as linux, reference links for minikube:
1. Install minikube: https://k8s-docs.netlify.app/en/docs/tasks/tools/install-minikube/
2. Start minikube: 
  a. minikube start
  b. alias kubectl="minikube kubectl --" (adding cmds via alias)
  c. minikube dashboard & (start dashboard if required, optional step)
  d. minikube tunnel (compulsory to allow and test LoadBalancer resources under minikube)
