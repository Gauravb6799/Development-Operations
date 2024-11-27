## LoadBalancer

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
  type: LoadBalancer
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

![image](https://github.com/user-attachments/assets/ae963a25-6651-4a64-8562-958a1fce300c)

