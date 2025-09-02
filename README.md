Docker & Kubernetes Homework 

1.	Project Layout 
 
     App is a simple Flask web app and prints Hello, World.

2.	Building the image
Ran into multiple issues for some reason and resorted to using nerdctl and taking the image with localhost/ .
nerdctl build -t localhost/flask-hello:latest .

3.	Running the container
Running the container is done with
nerdctl run --rm -p 5000:5000 --name hello-test localhost/flask-hello:latest


4.	Kubernetes 
The Kubernetes manifests are deployment.yaml and service.yaml
  

5.	Deployment
Deployment is done as such:
kubectl create ns demo 2>$null
kubectl -n demo apply -f k8s/
Watching the pod is done as such:
kubectl -n demo get pods -l app=flask-hello -w

6.	Accessing the app
By forwarding the port:
kubectl -n demo port-forward svc/flask-hello-service 8080:5000 (available at http://localhost:8080)
or simply  http://localhost:3007
