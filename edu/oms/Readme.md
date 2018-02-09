High level steps for setting up Log Analytics (OMS)

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
kubectl create -f oms-daemonset.yaml 