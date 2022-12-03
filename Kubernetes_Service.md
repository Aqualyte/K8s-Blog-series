# What is meant by Service in Kubernetes ?

By default your application running in the pods are not availabel for outside world in order to make your application available to outside **services** are being used which routes the traffic to contianer into the pod. Services is a machanism which exposes you pod on a network. There are three service which are used :

- NodePort
- ClusterIP
- LoadBalancer

### NodePort
