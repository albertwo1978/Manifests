Simple ingress controller example. Used the following blog as a guide. Since I am not testing hybrid (Windows and Linux) I did not follow the steps to create a separate agent pool or create the customer web apps. I instead replace the last steps with a guestbook app and two sample apps. Examples apps and high level setup instructions are located in their respective sub-directories. The nginx.yaml file is not currently used and can be ignored:

https://github.com/dougperkes/azure-acs-hybrid-cluster-migration

After building this out, I deploy the following three apps behind the ingress controller:
  1) Sample guestbook apps
  2) Two sample apps - Instructions on how to build and containerize the demo apps are in the Readme. 

Final step, I set up monitoring with both OMS and Prometheus - Very rudimentary setup (all default). Steps taken are in the monitoring sub-directory. 
