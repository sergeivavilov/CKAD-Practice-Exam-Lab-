# CKAD-Practice-Exam-Lab-
1. 

CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
4%
completed
1:55:49left
Challenge

Show hint

Watch video

Topic: ServiceAccount, Deployment

Context:

The spaceship crew has created a new Deployment named alfred for automating the search of new planets. In order to securely access resources for searching the crew decided to create a ServiceAccount and associate it with the Deployment.

Task:

Update the Deployment alfred in the kube-ship-system namespace to use existing ServiceAccount alfred-sa



----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


vi ~/kubeship/1/alpha-1-deployment.yaml 
kubectl apply -f ~/kubeship/1/alpha-1-deployment.yaml
 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2. 


CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
4%
completed
1:55:01left
Challenge

Show hint

Watch video

Topic: ServiceAccount, Deployment

Context:

The spaceship crew has created a new Deployment named alfred for automating the search of new planets. In order to securely access resources for searching the crew decided to create a ServiceAccount and associate it with the Deployment.

Task:

Update the Deployment alfred in the kube-ship-system namespace to use existing ServiceAccount alfred-sa
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


kubectl get deployment alfred -n kube-ship-system -o yaml > alfred-deployment.yaml
vi alfred-deployment.yaml
kubectl apply -f alfred-deployment.yaml

 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


3.




CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
16%
completed
1:30:18left
Challenge

Show hint

Watch video

Topic: Logs

Task:

A pod within the Deployment named hyper-v and in namespace non-critical-systems is logging errors.

1. Look at the logs to identify error messages. 
Tip: Find errors including User "system:serviceaccount:non-critical-systems:default" cannot list resource "pods" [...] in the namespace "non-critical-systems"

2. Update the Deployment hyper-v to resolve the errors in the logs of the Pod. 
Info: The hyper-v‘s manifest files can be found at ~/kubeship/3/hyper-v-deployment.yaml 
 

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

kubectl logs -l app=hyper-v -n non-critical-systems
cat ~/kubeship/3/hyper-v-deployment.yaml
kubectl get serviceaccount hyper-v-sa -n non-critical-systems
kubectl create serviceaccount hyper-v-sa -n non-critical-systems


    Step 4: Create RBAC Role and RoleBinding
Create a role to allow the service account to list pods:

vi role.yaml 

kubectl apply -f role.yaml

vi rolebinding.yaml
kubectl apply -f rolebinding.yaml



or (you can read file 1.txt) 





vi ~/kubeship/3/hyper-v-deployment.yaml 


kubectl apply -f ~/kubeship/3/hyper-v-deployment.yaml

kubectl logs -l app=hyper-v -n non-critical-systems


 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


4.   




CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
16%
completed
1:20:55left
Challenge

Show hint

Watch video

Topic: Pod with Resources

Context:

The crew captain asked you to create a Pod that requests a certain amount of CPU and memory.

Task:

Create a Pod named novanet-resources in the existing warp namespace.

Specify a single container using the nginx:stable image.

Specify a resource request of 400m cpus and 1Gi of memory for the Pod's container.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


 vi novanet-resources.yaml
 cat novanet-resources.yaml 
kubectl apply -f novanet-resources.yaml
 kubectl get pods -n warp





----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


5.





CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
20%
completed
1:17:33left
Challenge

Show hint

Watch video

Topic: Deployment , Environment variables

Context:

The leader of gravity-grid corps asked you to create a new Deployment for running NGINX

Task:

1. Create a Deployment called lunar in the existing gravity-grid namespace running 6 replicas of a Pod. Specify a single container using the Ifccncf/nginx:1.12.2 image. 
2. Add an environment variable named NGINX_PORT with value 8080 to the container then expose port 8080. 


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

vi lunar-service.yaml
kubectl apply -f lunar-service.yaml
kubectl get svc -n gravity-grid
kubectl get nodes -o wide

kubectl create secret docker-registry myregistrysecret \
--docker-server=YOUR_REGISTRY_SERVER \
--docker-username=YOUR_REGISTRY_USERNAME \
--docker-password=YOUR_REGISTRY_PASSWORD \
--docker-email=YOUR_REGISTRY_EMAIL \
-n gravity-grid


vi lunar-deployment.yaml
kubectl apply -f lunar-deployment.yaml
kubectl get pods -n gravity-grid -l app=lunar
kubectl describe pod -n gravity-grid -l app=lunar






----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


6.



CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
12%
completed
0:03:53left
Challenge

Show hint

Watch video

Topic: API-deprecation, Deployment

Context:

You are asked to deploy an application developed for an older version of Kubernetes on a cluster running a recent version of Kubernetes.

Task:

1. Fix any API-deprecation issues in the manifest file ~/kubeship/6/orion-ops.yaml so that the application can be deployed on the cluster. 
Info: The application was developed for Kubernetes `v1.15`. The cluster k8s runs recent version of Kubernetes
2. Deploy the application specified in the updated manifest file ~/kubeship/6/orion-ops.yaml in namespace celestial-core. 




----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

vi ~/kubeship/6/orion-ops.yaml
kubectl apply -f ~/kubeship/6/orion-ops.yaml -n celestial-core
kubectl get deployment orion-ops -n celestial-core
kubectl get pods -n celestial-core
kubectl describe deployment orion-ops -n celestial-core
kubectl get pods -n celestial-core
kubectl logs orion-ops-123abc -n celestial-core

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


7.




