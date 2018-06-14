Two sample apps built in Ubuntu 16.04, containerized and published to Docker Container Registry. High level instructions for creating those apps are below. I created the apps to stand up behind the ingress controller.

-- Used these steps below to create a simple Python App called app.py --

1) Create a directory to build the app in and cd into it. 

2) Used these steps to create the app. To keep it simple, I stopped before creating the Signup Page. If I add to this, I will update the Readme. 

https://code.tutsplus.com/tutorials/creating-a-web-app-from-scratch-using-python-flask-and-mysql--cms-22972

3) Created the Dockerfile in the application folder - 

FROM python:2
ADD ./ /
RUN pip install flask
ENTRYPOINT [ "python", "./app.py" ]

4) Ran the following steps to create the container image and publish to Docker registry: 

docker build -t <new_image_name> .

#To test, you can run the following command locally which creates the container and maps it to host port 5000

docker run --name <new_container_name> -p 5000:5000 -d <new_image_name>

#Push the image to Docker registry - You will need to run "docker login" first 
#If you do not have a Docker account, you will need to create that before moving on. Don't worry. It's free. 

docker tag <new_image_name> <docker_id>/<new_image_name>
docker push <docker_id>/<new_image_name>



--Used these steps below to create a simple Node App called app.js --

1) Create a directory to build the app in and cd into it. 

2) Created an app called app.js in the directory. Below is the app code. Super simple:

const http = require('http');
const os = require('os');

console.log("Server starting...");

var handler = function(request, response) {
  console.log("Received request from " + request.connection.remoteAddress);
  response.writeHead(200);
  response.end("You've hit " + os.hostname() + "\n");
};

var www = http.createServer(handler);
www.listen(8080);

3) Created the Dockerfile in the application folder - 

FROM node:7
ADD app.js /app.js
ENTRYPOINT ["node", "app.js"]

4) Ran the following steps to create the container image and publish to Docker registry (same as step 4 above): 

docker build -t <new_image_name> .

#To test, you can run the following command locally which creates the container and maps it to host port 8080

docker run --name <new_container_name> -p 8080:8080 -d <new_image_name>

#Push the image to Docker registry -  

docker tag <new_image_name> <docker_id>/<new_image_name>
docker push <docker_id>/<new_image_name>

#In case you haven't read them, I highly recommend Kubernetes Up and Running and Kubernetes In Action. Both great reads to level up! 
