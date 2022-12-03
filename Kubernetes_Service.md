# What is meant by Service in Kubernetes ?

By default your application running in the pods are not availabel for outside world in order to make your application available to outside **services** are being used which routes the traffic to contianer into the pod. Services is a machanism which exposes you pod on a network. There are three service which are used :

- NodePort
- ClusterIP
- LoadBalancer

### NodePort

![image](https://user-images.githubusercontent.com/69069614/205437185-296cf220-fd10-43e6-a778-36b08aa23292.png)

### ClusterIP

![image](https://user-images.githubusercontent.com/69069614/205437234-86c5d379-422c-4296-b0e0-d6ec6b6f0f5b.png)


### LoadBalancer

![image](https://user-images.githubusercontent.com/69069614/205437209-44a2dcb9-ae8f-4a07-8c00-15318387b861.png)
