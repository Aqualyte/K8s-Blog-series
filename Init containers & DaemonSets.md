# What are InitContainers?

InitContainers are same as normal container only difference is the perfom the certiain task before the main contianer starts. Initcontainers are not running for longer period of time like other containers once the init container task is done it no longer running. After the task completes main container starts. There can be multiple init containers and can run one by on and completes the task.

![image-removebg-preview](https://user-images.githubusercontent.com/69069614/206639515-748ac96d-2b3f-444e-9c0d-fc1d5ceb4f90.png)


# What is use of InitContainers? and When to use InitContainers ?

InitContainers are used to perform some task before starting the main containers. These task maybe related to changing file permission for some specific environment, also they can be use to precheck of file for starting the application. There may be some tasks that only the root user can do. And since you never want to run your application as a root user as this is a security threat. Init containers can do the task for you that you wanted to run as a root user.

InitContainers cater for dedicated pre-run tasks that depend on tooling outside your main container image. 

Below are the Few sitiuations where you might use InitConyainers: 

- Generating any configuration file from environment variables.
- Installing any plugins in to volumes which might reqired for application.
- Blocking application startup until dependencies are available.

One limitations that InitContainers are having that you cant assign any kind of liveness or rediness probe. These are the separate mechanism which are used with main containers.

# InitContainers manifest File

```
apiVersion: v1
kind: Pod
metadata:
  name: myapp
spec:
  initContainers:
  - name: init-con1
    image: busybox:1.28
    command: ['sh', '-c', 'echo The app is running! && sleep 3600']
  containers:
  - name: con1
    image: busybox
 ```
