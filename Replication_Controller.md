## Replication Controller: (RC)
Replication controller is used to manage and create replication and scaling pods.
A Replication Controller in Kubernetes is a legacy API object responsible for ensuring that a specified number of pod replicas are running at any given time. 
It helps maintain the desired state of the application by creating or deleting pods as needed.

**Selector**
selector is a set of labels that identify the pods that a replication controller manages.
The replication controller uses the selector to determine how many pod instances are running and to adjust as needed
**There are two types of selector**
1. Equality based (Key Value Pair) : this selector is used in Replication Controller
2. Set Based
   i. IN
   ii. Not In
   iii. Exist

````
apiVersion: v1
kind: ReplicationController
metadata:
 name: rc-01

spec:
 replicas: 3
 selector:
    app: demoapp
 template:
   metadata:
    labels:
      app: demoapp
   spec:
    containers:
    - name: cont-1
      image: nginx
      ports:
      - containerPort: 80
````
