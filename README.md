# networking-kubernetes

Project: Networking in Kubernete.




-This refers to a mechanism or configuration that allows communications between different components (pods, services and other resources) within a kubernete cluster. Kubernete provides a flexible and powerful networking model to enable seamless interaction between container and services.
Some key aspects of networking are



-Pod networking




-Service networking.



-Pod-to-pod communication.



-Ingress



-Network policy



-I created a YAML multi container pod by running the below
     * apiVersion: v1
kind: Pod
metadata:
  name: multi-container-pod
spec:
  containers:
  - name: container-1
    image: nginx:alpine
  - name: container-2
    image: busybox
    command:
      - '/bin/sh'
      - '-c'
      - 'mkdir -p /usr/share/nginx/html && while true; do echo "Hello from Container 2" >> /usr/share/nginx/html/index.html; sleep 10; done'




-apiVersion: specifies api version to be created.



-kind:pod: defines the type of kubernete beign created which is a pod.


-metadata: which contains metadata for the pods, including name of the pods.



-specs: describe the desired state of the pods.



-containers: specifies the container configuration for the pods.



-name container 1


-name container 2



-To apply pod configurations, I ran the command below.
        * kubectl apply -f multi-container-pod.yaml



-To check pod status I used the command below
         * kubectl get pods
kubectl logs multi-container-pod -c container-1
kubectl logs multi-container-pod -c container-2




-To access ngninx from BusyBox container I ran the below command
            * kubectl exec -it multi-container-pod -c container-2 -- /bin/sh



-Within the BusyBoX container, I used curl.




-This project has given me more insight into kubernete networking. Though tough, but was able to pull through with the help of the internet resources.

