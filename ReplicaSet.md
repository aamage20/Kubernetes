## Replica Set:(RS)
A ReplicaSet in Kubernetes is an API object that ensures a specified number of identical pod replicas are running in a cluster. It is the successor to the Replication Controller and offers additional capabilities, such as more flexible label selectors.

- Replica set is resource that ensure a specified number of pods are running at all time
- It is designed to manage Pod replications.
- In this selectors Equality based and Set based both selectors are used.

## Differences Between ReplicaSet and Replication Controller
![image](https://github.com/user-attachments/assets/8aaa6f2f-1dea-4e3c-ad29-dab26a5ab035)

````

apiVersion: apps/v1
kind: ReplicaSet
metadata:
 name: rs-demo
spec:
 replicas: 3
 selector:
  matchExpressions:
   - key: app
     operator: In
     values:
     - demoapp
     - dev

 template:
  metadata:
   name: template-01
   labels:
    app: demoapp
    env: dev
  spec:
   containers:
   - name: cont-01
     image: nginx
     ports:
     - containerPort: 80
````
