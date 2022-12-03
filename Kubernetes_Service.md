# What is meant by Service in Kubernetes ?

By default your application running in the pods are not availabel for outside world in order to make your application available to outside **services** are being used which routes the traffic to contianer into the pod. Services is a machanism which exposes you pod on a network. There are three service which are used :

- NodePort
- ClusterIP
- LoadBalancer

### NodePort

In this type of service you are allowing the external traffic by opening TCP port of your worker node and via kube-proxy which available in all node will proxy requests from the TCP port to the pod on this node.

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

Now you can simply apply the above YAML file to create service.

To check the service type :

```
kubectl get svc mysvc
```

### ClusterIP

![image](https://user-images.githubusercontent.com/69069614/205437234-86c5d379-422c-4296-b0e0-d6ec6b6f0f5b.png)


### LoadBalancer

![image](https://user-images.githubusercontent.com/69069614/205437209-44a2dcb9-ae8f-4a07-8c00-15318387b861.png)
