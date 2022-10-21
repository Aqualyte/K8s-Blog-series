# What is Replicaset ?

Replicaset object is use to maintain a stable set of replicated pods running within a cluster at any given time. Its purpose is to maintain the specified number of pods and prevent the user from loosing the control of the application incase of any pod failure or inaccessible. Whenever any pod gets failed replicaset immidiatly launces another pod and replacing it with failed pod.

![rs4](https://user-images.githubusercontent.com/69069614/197024265-d1a65708-af00-41ba-958c-10fadf672fe7.png)

**Replicaset has following features:**
- A pod template is used to create a new pod whenever a existing pod fails and also replica count is also maintain by defining the desired number of replicas that a controller needs to be running.
- A replicaset also ensures that additional pod need to be created or deleted whenever instance whith same label is created.
- Replcaset allows to have multiple replicas of pod which means that the traffic is sent to different instances which prevents single instance from being overloaded.
- Replcaet ensures it has multiple replicas of application so that it wont fail because of one pod fails.

# Replicaset Configuration

**Below is the yaml file which will create multi replicas of pod.**

```
---
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: httpd-replica
  namespace: facebook
spec:
  replicas: 4
  minReadySeconds: 10
  selector:
    matchLabels:
      role: web
    matchExpressions:
      - {key: version, operator: In, values: [v1, v2, v3]}
  template:
    metadata:
      name: web
      labels:
        role: web
        version: v1
        tier: frond
    spec:
      containers:
      - name: web
        image: httpd
        ports:
        - containerPort: 80
          protocol: TCP
```

**Fields that are use to define replicaset are as follows:**

- **Selector:** It is used to identify for which pod the replicaset is responsible for.
- **Replicas:** It specifies the number of pods which replicaset has to maintain.
- **Template:** It defines he pod template that replicaset will use in order to create new pods.
- **ApiVersion:** It defines kubernetes API that supports ReplicaSet.

# What is Deployment ?

![image](https://user-images.githubusercontent.com/69069614/197216181-fb953a23-60f9-4131-8392-2c7818fb6134.png)


# Deployment with Replicaset




