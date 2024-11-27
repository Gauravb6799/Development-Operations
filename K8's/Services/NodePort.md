### Node Port Range 30000 - 32767

````
apiVersion: v1
kind: Pod
metadata:
 name: frontend
 labels:
   app: frontend-app
spec:
  containers:
  - name: c1
    image: abhipraydh96/docker-app
    ports:
    - containerPort: 80

---
apiVersion: v1
kind: Service
metadata:
  name: net-service
spec:
  selector:
    app: frontend-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: NodePort
````

**NodePort demo with nodeport number**
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

![image](https://github.com/user-attachments/assets/ac0301a6-ba84-4980-b11d-58cc9bfdfebc)


