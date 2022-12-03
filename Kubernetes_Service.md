# What is meant by Service in Kubernetes ?

By default your application running in the pods are not availabel for outside world in order to make your application available to outside **services** are being used which routes the traffic to contianer into the pod. Services is a machanism which exposes you pod on a network. There are three service which are used :

- NodePort
- ClusterIP
- LoadBalancer

### NodePort

In this type of service you are allowing the external traffic by opening TCP port of your worker node and via kube-proxy which available in all node will proxy requests from the TCP port to the pod on this node. Behind it will create the ClusterIP which will route the traffic from this ClusterIP to the port. Internally loadbalancing will performed to divert traffice to different pods in the node.

![image](https://user-images.githubusercontent.com/69069614/205437185-296cf220-fd10-43e6-a778-36b08aa23292.png)

**NodePort Type:**

- Will be tied up with you host eg: EC2.
- Depends on host, if host is not available then this service won't work.
- it will provide access to the pod only to same worker node.
- NodePort will allocate th port the port range 30000-32767

**NodePort Manifest File:**

```
apiVersion: v1
kind: Service
metadata:
  name: mysvc
spec:
  ports:
  - port: 80
    nodePort: 30123
  selector:
    app: myapp
  type: NodePort

```

Now you can simply apply the above YAML file to create service. To check the service type :

```
kubectl get svc mysvc
```

### ClusterIP

This is the default type of service when you create any service and if yo didn't specify any type ClusterIP will be the defaultly allocated but this will be available internally to the pod to communicate with each other. Application can internally communicate within cluster without any access from outside world.

![image](https://user-images.githubusercontent.com/69069614/205437234-86c5d379-422c-4296-b0e0-d6ec6b6f0f5b.png)

It will use IP's from the IP-pool and will be accessible via a DNS-name in the cluster’s scope.

**ClusterIP Manifest file:**

```
apiVersion: v1
kind: Service
metadata:
  name: mysvc
spec:
  ports:
  - port: 80
  selector:
    app: myapp
  type: ClusterIP
```

Here type is optional even if you won't specify it will create ClusterIP defaultly.

Yo can apply the above yaml file and Check:

```
kubectl get svc mysvc
```

### LoadBalancer

This is the most common used service but this can used only with the managed kubernetes like GKS, AKS, EKS. In case of AWS it will create a classic load balancer in which it will route the traffic to the EC2 node and via Nodeport service to all pods.

![image](https://user-images.githubusercontent.com/69069614/205437209-44a2dcb9-ae8f-4a07-8c00-15318387b861.png)

**LoadBalancer Type:**

- Will provide external access to pod.
- provides the load balancing to the nodes.

**LoadBalncer Manifest File:**

```
apiVersion: v1
kind: Service
metadata:
  name: mysvc
spec:
  ports:
  - port: 80
  selector:
    app: myapp
  type: LoadBalancer
```

If you aare not using any managed kuberenets and creating service with loadbalancer then it will simply create the service and won't show any error but it can't be used.

By applying the above file you will get external ip form the cloud provider IP pool which you can access. To check the service created :

```
kubectl get svc mysvc
```
