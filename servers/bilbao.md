## Scenario: "Bilbao": Basic Kubernetes Problems
 
 *Description*: There's a Kubernetes Deployment with an Nginx pod and a Load Balancer declared in the manifest.yml file. The pod is not coming up. Fix it so that you can access the Nginx container through the Load Balancer.

 ### Solution 

The issue was first that the NodeSelector was not matching the worker node, then the next issue was that the machine had insufficient memory because of the manifesto asking for 2gb ram to start and the machine only had 1gb.

After changing those things and `kubectl apply -f ./manifest.yml` the pod was up and running