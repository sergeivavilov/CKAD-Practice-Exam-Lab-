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



--------------------------------------------------------------


vi ~/kubeship/1/alpha-1-deployment.yaml 
kubectl apply -f ~/kubeship/1/alpha-1-deployment.yaml
 
--------------------------------------------------------------

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
--------------------------------------------------------------


kubectl get deployment alfred -n kube-ship-system -o yaml > alfred-deployment.yaml
vi alfred-deployment.yaml
kubectl apply -f alfred-deployment.yaml

 
--------------------------------------------------------------


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
 

--------------------------------------------------------------

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


 
--------------------------------------------------------------





