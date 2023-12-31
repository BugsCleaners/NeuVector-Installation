Using helm:

Visit the link to view the helm charts and values(its on charts/core): [neuvector helm chart link](https://github.com/neuvector/neuvector-helm/tree/master/charts/core)  

After that adjust the following in the values file:  
	• Change the service type to "loadbalancer"  
	• Change the containered flag to true (if we are using a gke)  

Then upload the updated value file (ex: nu-values.yaml) to where you want to deploy the neuvector and use the below command:  
	• helm install neuvector neuvector/core -n neuvector --create-namespace -f nu-values.yaml  

Then make sure that the webui service (which will be connected to the manager) is up, and note the external IP:  
	• Kubectl get svc -n neuvector   

Then login to the gui using: https://<external-ip>:8443  

	• Tip: enable auto-scan, and give it time to scan the containers (try re login)  
	• It only scan kubernetes containers in the cluster (list them using: kubectl get pod)  
  
Select the vulnerabilities tab, and while highlighting any vulnerability it will shows the affected package version, and the fixed version, in addition at what pod the vulnerability exists.  

  
Reference: [how to install neuvector](https://www.youtube.com/watch?v=c7cF0M4VIX8)  



