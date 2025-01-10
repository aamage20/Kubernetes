## In Kubernetes, a Service is a method for exposing a network application that is running as one or more Pods in your cluster.

**Types:**
1. clusterIP
2. NodePort
3. LoadBalancer

**1.ClusterIP:**
ClusterIP is a service type in Kubernetes used to expose an application running on a set of pods within a Kubernetes cluster. 
It allows other services within the cluster to communicate with the application using an internal IP address that is accessible 
only within the cluster.

````
apiVersion: apps/v1
kind: Deployment
metadata:
  name: app2
spec:
  replicas: 1
  selector:
    matchLabels:
      app: app2
  template:
    metadata:
      labels:
        app: app2
    spec:
      containers:
        - name: app2-container
          image: nginx
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: app2-service
spec:
  selector:
    app: app2
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
````


**2.NodePort:**
NodePort is a type of Kubernetes service that exposes an application running in a cluster to external traffic. 
It allows external users to access a service using a port on each node of the cluster.

### Node Port Range 30000 - 32767

````
apiVersion: apps/v1
kind: Deployment
metadata:
  name: app1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: app1
  template:
    metadata:
      labels:
        app: app1
    spec:
      containers:
        - name: app1-container
          image: nginx
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: app1-service
spec:
  selector:
    app: app1
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: NodePort
````

**using NodePort**
````
apiVersion: v1
kind: Service
metadata:  
  name: my-nodeport-service
spec:
  selector:    
    app: my-app
  type: NodePort
  ports:  
  - name: http
    port: 80
    targetPort: 80
    nodePort: 30036
    protocol: TCP
````

**Commands:**
````
kubectl apply -f node-deploy.yaml
````
````
kubectl get deploy
kubectl get svc
kubectl get pod
````
````
kubectl get node -o wide
````
![image](https://github.com/user-attachments/assets/2e160b9e-7612-43d7-a560-336301f1a7cf)


![Screenshot 2025-01-10 144105](https://github.com/user-attachments/assets/c32b9a72-aed6-4c47-8650-10b32ca51caf)


**3.LoadBalancer:**
LoadBalancer is a type of Kubernetes service that exposes your application to external traffic by integrating with a cloud provider's load balancer.
It is the easiest way to expose a service externally in a cloud environment.
````
apiVersion: v1
kind: Service
metadata:
  name: my-loadbalancer-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80          # External port exposed by the load balancer
      targetPort: 8080  # Pod's internal port
  type: LoadBalancer
````

