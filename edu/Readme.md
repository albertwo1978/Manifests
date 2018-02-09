Simple ingress controller example. Used the following blog as a guide. Since I am not testing hybrid (Windows and Linux) I did not follow the steps to create a separate agent pool and instead replace his last steps with a simple Nginx website that site behind the ingress controller(nginx.yaml):

https://github.com/dougperkes/azure-acs-hybrid-cluster-migration

After building this out, I deploy the following two apps behind the ingress controller:
  1) Sample guestbook apps
  2) Two sample apps - Instructions on how to build and containerize the demo apps are in the Readme. 
