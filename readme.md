**expense**
----------
trainee --> read access
senior engineer --> deployment access
team lead --> namespace admin
manager --> cluster admin access

User, Role(Resources and actions), Rolebinding (bind the user and role)

EKS uses IAM for authentication

EKS --> Platform as a service

**Authentication**
--------------
I need to create user in IAM named Suresh

**Suresh joined our team**
-----------------------
Expense team will send an email to EKS admin ro create an iam role for this suresh user >>

give him read access to expense namespace

they create IAM user Suresh, create a role for suresh to describe eks cluster.. Create policy in cluster to describe the cluster


they create role and rolebinding
provide access to suresh

EKS and IAM are two different systems

there is something called aws-auth config map inside kube-system
configure the aws-auth manually by adding users
>>**kubectl get configmap aws-auth -n kube-system -o yaml**

then login to the user account and install kubectl there to access cluster
>> **aws eks update-kubeconfig --region us-east-1 --name expense**

>>**kubectl config set-context --current --namespace=expense**

IAM checks whether user have expense EKS cluster access or not

taints and tolerations
affinity and anti affinity

kube-scheduler --> master node component

kubectl apply -f manifest.yaml

nodeSelector:
	az: us-east-1b
	
taint --> paint
banks and RBI may accept painted notes --> they can tolerate

you can taint the node. kube-scheduler can't schedule any pod in that node...
GPU based servers are required for expense project...

taint these GPU nodes
expense project users should give toleration in their manifest files

1. EKS is integrated with IAM for authentication
2. aws-auth configmap

1. make sure IAM user exist and he have cluster describe access
2. create role and rolebinding
3. edit aws-auth configmap