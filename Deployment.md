## Deployment:
A Deployment in Kubernetes is a higher-level abstraction that manages the lifecycle of applications running on a set of pods. 
It provides declarative updates, meaning you can define the desired state (such as the number of replicas, image version, etc.), 
and Kubernetes ensures that the state is achieved and maintained.

- Deployment support rolling updates: Upgrade to new version
- Deployment support rollback : downgrad to previous version
- Deployment are commonly used for the resources managing stateless application in kubernetes.


  ````
apiVersion: apps/v1
kind: Deployment
metadata:
 name: deployment-1
spec:
 replicas: 5
 selector:
  matchLabels:
   app: demoapp

 template:
  metadata:
   name: template-01
   labels:
    app: demoapp
  spec:
   containers:
   - name: cont-01
     image: nginx
     ports:
     - containerPort: 80
````
