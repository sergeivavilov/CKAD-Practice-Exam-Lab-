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


CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
12%
completed
0:02:47left
Challenge

Show hint

Watch video

Topic: Secret, Pod consuming a Secret

Context:

The crew is planning a mission that involves sensitive data that needs to be stored securely.

You are asked to create a Secret and consume it in a Pod.

Task:

1. Create a Secret named space-sentry-secret in the kube-ship-system namespace containing the following single key-value pair:
    key-value:

        `dest: astro`
2. Create a pod named space-sentry in the kube-ship-system namespace. Specify a single container using the httpd:2.4.41-alpine image. 
Add an environment variable named DESTINATION consuming the value of the secret key dest



task : 

Create a Secret named 'space-sentry-secret' containing the 'dest: astro' key-value pair
Add an environment variable named 'DESTINATION'
Variable named 'DESTINATION' should consume the value of the secret key 'dest'
Specify a single container using the 'httpd:2.4.41-alpine' image



----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

kubectl create secret generic space-sentry-secret --from-literal=dest=astro -n kube-ship-system
vi space-sentry.yaml
kubectl apply -f space-sentry.yaml
kubectl get secrets -n kube-ship-system
kubectl describe secret space-sentry-secret -n kube-ship-system
kubectl get pods -n kube-ship-system
kubectl describe pod space-sentry -n kube-ship-system

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



8.



CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
12%
completed
1:31:41left
Challenge

Show hint

Watch video

Topic: Deployment

Context:

You are asked to update an application and then perform a rollback of that update.

Task:

1. Update the proportional scaling configuration of the Deployment rocket in the non-critical-systems namespace setting maxSurge to 4 and maxUnavailable to 4. 
2. Update the rocket Deployment to use version tag 1.31 for the busybox container image. 
3. Perform a rollback of the app Deployment to its previous version.



task 

Set maxSurge to 4
Set maxUnavailable to 4
Update the Deployment to use version tag '1.31' for the 'busybox' container image
Perform a rollback of the Deployment to its previous version


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

kubectl edit deployment rocket -n non-critical-systems

look this file for correct 
fixed-rocket-deployment.yaml


kubectl rollout status deployment/rocket -n non-critical-systems
kubectl rollout undo deployment/rocket -n non-critical-systems
kubectl rollout status deployment/rocket -n non-critical-systems
kubectl rollout history deployment/rocket -n non-critical-systems

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


9. 50% !!!!!



CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
12%
completed
1:30:26left
Challenge

Show hint

Watch video

Topic: SecurityContext

Task:

Modify the existing Deployment named cosmic-whale, running in a namespace star-stream, so that its containers:

1) run with user ID `20000` and 

2) privelege escalation is forbidden
Info: the cosmic-whale manifest file can be found at ~/kubeship/9/cosmic-whale.yaml


weight: 4%

Modify the existing Deployment so that its containers run with user ID '20000'
Modify the existing Deployment so that privelege escalation is forbidden for its containers


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

vi ~/kubeship/9/cosmic-whale.yaml
kubectl apply -f ~/kubeship/9/cosmic-whale.yaml
kubectl describe pod -l app=cosmic-whale -n star-stream


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

10.




CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
5%
completed
1:20:53left
Challenge

Show hint

Watch video

Context:

The spaceship crew created a Pod that should be allowed to communicate with two other Pods but nothing else.

Task:

Update the Pod lunar-lander in the astro-link namespace to use a NetworkPolicy allowing the Pod to send and receive traffic only to and from the Pods connect-pod and compute-pod.

Info: All required NetworkPolicies have already been created.
Reminder: You must not create, modify or delete any NetworkPolicy while working on this task. You may only use existing NetworkPolicies.
weight: 8%

Update the Pod lunar-lander to use a NetworkPolicy allowing the Pod to send and receive traffic only to and from the Pods connect-pod and compute-pod 1
Update the Pod lunar-lander to use a NetworkPolicy allowing the Pod to send and receive traffic only to and from the Pods connect-pod and compute-pod 2

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


11.

CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
16%
completed
0:48:21left
Challenge

Show hint

Watch video

Topic: CronJob, Job

Context:

A group of Astro Engineers need to periodically get a very long number for their calculations.

Task:

1. Create a CronJob named pi that executes a Pod running the following single container: 
name: pi

image: notmiddev30/pi:0.1

command: ["go", "run", "pi.go"]

Configure the Cronjob to:

1) execute once every 5 minutes 

2) keep 4 completed Job 

3) keep 5 failed Job 

4) never restart Pods 

5) terminate Pods after 10 seconds 
2. Manually create and execute one Job named pi-test from the pi CronJob for testing purposes. 
Info: It doesn't matter if the Job completes or fails


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

vi pi-cronjob.yaml
kubectl apply -f pi-cronjob.yaml
vi pi-test-job.yaml
kubectl apply -f pi-test-job.yaml
kubectl delete cronjob pi
kubectl apply -f pi-cronjob.yaml
kubectl delete job pi-test
kubectl apply -f pi-test-job.yaml

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


12.


CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
16%
completed
0:46:50left
Challenge

Show hint

Watch video

Topic: Ingress

Task:

A Deployment named orion-station-deploy, running in namespace galactix is exposed via Ingress orion-ingress.

Info: The manifest files for the Deployment, Service and Ingress can be found at ~/kubeship/12/ .
The Deployment is supposed to be reachable at http://k8s.local/orion-station, but requesting this URL is currently returning an error.

Identify and fix the problems by updating the associated resources so that the Deployment becomes externally reachable as planned.

Reminder: Don't modify the Deployment; you can assume the Deployment to be correct and functional. 
Info: You can use the following command to test the Deployment's reachability:

[student@node-1] $ curl -v http://k8s.local/orion-station

weight: 8%

The Deployment should become externally reachable at 'http://k8s.local/orion-station' 1
The Deployment should become externally reachable at 'http://k8s.local/orion-station' 2


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


13. 



CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
4%
completed
1:23:34left
Challenge

Show hint

Watch video

Topic: Pod with resources

Task:

The Pod for the Deployment named galactix-db in the milky-way namespace fails to start because its Container runs out of resources.

Update the galactix-db Deployment so that the Pod:

1) requests '160Mi' of memory for its Container 

2) limits the memory to half the maximum memory constraint set for the milky-way namespace 
Info: The galactix-db Deployment's manifest file can be found at ~/kubeship/13/galactix-db.yaml
weight: 8%

Update the 'galactix-db' Deployment so that the Pod requests '160Mi' of memory for its Container
Update the 'galactix-db' Deployment so that the Pod limits the memory to half the maximum memory constraint set for the milky-way namespace



----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

vi ~/kubeship/13/galactix-db.yaml
kubectl apply -f ~/kubeship/13/galactix-db.yaml



----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



14.



CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
12%
completed
1:04:28left
Challenge

Show hint

Watch video

Topic: Rollout Strategy, Deployment

Task:

A Service named stellar-service in the starfish namespace points to 5 Pods created by the Deployment named current-stellar-deployment.

architecture

Info: The current-stellar-deployment manifest file can be found at ~/kubeship/14/current-stellar-deployment.yaml
1. Create an identical Deployment, named canary-stellar-deployment, in the same namespace. 

2. Modify the Deployments so that: 

  1) a maximum number of 10 Pods run in the 'starfish' namespace. 

  2) 30% of the 'stellar-service' traffic goes to the canary-stellar-deployment Pods.
architecture

Info: The Service is exposed on NodePort '30000'. To test its load-balancing, run:

[student@node-1] $ curl http://k8s-cp:30000/

weight: 8%

% of the 'stellar-service' traffic goes to the 'canary-stellar-deployment' Pods
Other part of the 'stellar-service' traffic goes to the 'current-stellar-deployment' Pods
A maximum number of 10 Pods run in the 'starfish' namespace



----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

cp ~/kubeship/14/current-stellar-deployment.yaml ~/kubeship/14/canary-stellar-deployment.yaml
vi ~/kubeship/14/canary-stellar-deployment.yaml
  
     In the editor, change the name of the deployment to canary-stellar-deployment or check file canary-stellar-deployment.yaml



vi ~/kubeship/14/starfish-quota.yaml 
                 check starfish-quota.yaml 


kubectl apply -f ~/kubeship/14/canary-stellar-deployment.yaml



kubectl describe svc stellar-service -n starfish
kubectl describe deployment current-stellar-deployment -n starfish
kubectl describe deployment canary-stellar-deployment -n starfish
         # 70% traffic to the original, 30% to the canary
kubectl scale deployment current-stellar-deployment --replicas=7 -n starfish
kubectl scale deployment canary-stellar-deployment --replicas=3 -n starfish
kubectl describe svc stellar-service -n starfish
curl http://k8s-cp:30000/

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




15. 50%



CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
15%
completed
0:35:03left
Challenge

Show hint

Watch video

Topic: Dockerfile

Task:

A Dockerfile has been prepared at ~/kubeship/15/build/Dockerfile.

1. Using the prepared Dockerfile, build a container image with the name space-cat and tag '1.1'. You may install and use the tool of your choise. 
Info: Multiple image builders and tools have been pre-installed in the base system, including: 'docker', 'skopeo', 'buildah', 'img', and 'podman'.
Reminder: Please do not push the built image to a registry, run a container, or otherwise consume it. 
2. Using the tool of your choise, export the built container image in OCI-format and store it at ~/kubeship/15/images/space-cat-1.1.tar . 
weight: 8%

Using the prepared Dockerfile, build a container image with the name 'space-cat' and tag '1.1'
Export the built container image in OCI-format and store it at '/opt/kubeship/15/images/space-cat-1.1.tar'



----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
cd ~/kubeship/15/build/

sudo docker build -t space-cat:1.1 .
sudo docker images


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------






16. 50 % !!!




CKAD Practice Exam
Lab launched. It will end if the time runs out or you press the "Finish" button in the last task.
2%
completed
1:54:54left
Challenge

Show hint

Watch video

Task:

First update the Deployment starblaze-deployment in the starblaze namespace:

1. To run 3 replicas of the pod
Add the following label on the pod:

    star: thousand 
Next, create a NodePort Service named nebula in the starblaze namespace exposing the starblaze-deployment Deployment on TCP port 8888


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
kubectl edit deployment starblaze-deployment -n starblaze

look  starblaze-deployment.yaml
kubectl get deployment -n starblaze

vi nebula-node.yaml
kubectl apply -f nebula-node.yaml

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

