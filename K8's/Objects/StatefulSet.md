## Statefulset
- This is useful for managing applications that need persistent storage or a stable, unique network identity.
**statefulset provides**
- Stable, unique network identifiers.
- Stable, persistent storage.
- Ordered, graceful deployment and scaling.
- Ordered, automated rolling updates.




````
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: redis
spec:
  serviceName: "redis"
  replicas: 3
  selector:
    matchLabels:
      app: redis
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
      - name: redis
        image: redis:5.0.5
        ports:
        - containerPort: 6379
          name: redis
  volumeClaimTemplates:
  - metadata:
      name: redis-data
    spec:
      accessModes: [ "ReadWriteOnce" ]
      resources:
        requests:
          storage: 1Gi
````

````
kubectl get sts
````
````
kubectl get pods
````
![image](https://github.com/user-attachments/assets/b7a2ecd8-e758-4a42-a925-18d032243077)

