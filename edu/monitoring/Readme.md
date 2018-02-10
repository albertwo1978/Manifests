High level steps for setting up monitoring - 

-- Option One - Prometheus with Grafana --

#prerequisites 
#install Helm
https://github.com/kubernetes/helm/blob/master/docs/install.md

#deploy Prometheus with helm
https://github.com/kubernetes/charts/tree/master/stable/prometheus

#set up ingress 
kubectl apply -f https://raw.githubusercontent.com/albertwo1978/Manifests/master/edu/monitoring/prometheus-ingress.yaml


-- Option Two - Log Analytics (OMS) --

#go here and follow directions to create Management Solution -> Log Analytics
https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-add-solutions

#once created, follow instructions here - you will need to go to the OMS portal, map it to the Log Analytics portal you created and get the Workspace ID and Key
https://docs.microsoft.com/en-us/azure/container-service/kubernetes/container-service-kubernetes-oms#installing-oms-on-kubernetes

#go here and run the command to generate the secret
https://github.com/lastcoolnameleft/workshops/blob/master/kubernetes/oms.md

#go here and copy the yaml for deploying the oms agent Daemon Set
#note - the previous link uses a slightly different secret name - 'oms-agent-secret'
https://raw.githubusercontent.com/Microsoft/OMS-docker/master/Kubernetes/omsagent-ds-secrets.yaml

#run this command in the same directory as the yaml file to deploy the daemonset 
kubectl apply -f oms-daemonset.yaml 

#navigate back to the OMS portal and create a Container Monitoring Solution
https://<name_used_for_log_analytics_in_step_one>.portal.mms.microsoft.com

#after you do this, you should also see a new Containers Solution in the same Resource Group where you create the Log Analytics Solution

#within a few minutes, you should see data populating

