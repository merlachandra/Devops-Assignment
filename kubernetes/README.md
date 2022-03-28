In this `kubernetes` directory below are details of the kubernetes resource files:

1. API deployment and service file to create pod and service for backend app based on flask framework
2. UI deployment and service file to create pod and service for frontend app based on react library.
3. Proxy server (nginx) file for local deployments like minikube for communicating outside the k8s cluster. 
Note: In minikube if ingress controller couldn't obtain external IP, we can define a port forward rule as below:
`kubectl port-forward pod/nginx-deployment-d6bd56576-25bmz 30100:80`

4. Ingress file to be used in cloud environments like Azure, where we can expose end-user interfaces using ingress on internet.

Note that #3 and #4 are mutually exclusive as both have redundancy for our usage.