# What is Replicaset ?

Replicaset object is use to maintain a stable set of replicated pods running within a cluster at any given time. Its purpose is to maintain the specified number of pods and prevent the user from loosing the control of the application incase of any pod failure or inaccessible. Whenever any pod gets failed replicaset immidiatly launces another pod and replacing it with failed pod.

![rs](https://user-images.githubusercontent.com/69069614/197015391-0033f3fd-8c46-4a09-92c3-686ea0fa142a.png)

**Replicaset has two main features:**
- A pod template is used to create a new pod whenever a existing pod fails and also replica count is also maintain by defining the desired number of replicas that a controller needs to be running.
- A replicaset also ensures that additional pod need to be created or deleted whenever instance whith same label is created.

**Kubernetes helps with the following:**
- **Load Balancing:** 





# What is Deployment ?



# Deployment with Replicaset




