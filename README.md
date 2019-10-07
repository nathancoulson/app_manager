# app_manager
App Manager and NGINX config of web app for MSc Data Science project repo (microservice auto-scaling system)

# Description
Application summary as part of test microservice based web application (seen in 2019 N C Coulson paper: "Adaptive microservice scaling for elastic web applications")

We used Docker Swarm, Docker’s container clustering and scheduling tool, to deploy App 1, App 2, App 3, App 4 and an NGINX container with a custom configuration file as an interconnected and scalable microservice based web application. The Dockerfiles which define how each of these Docker images should be built can be found in appendix F.
Each microservice was deployed as a Docker ”service” and connected on a common network. Each service can contain one or more containers. Requests received by the service are then load balanced, with Ingress, between the containers in that service. The configuration of these connected services was defined as a Docker ”stack”. This stack could be said to be the top level microservice based application in deployment. The YAML file which defines how this stack should be configured can be found in this repo.

# Deployment

Contains docker-compose file for micro app (bbk project)

Command to listen for logs:

- Create log text file

- Edit yml file to select the right number of containers

- Remove the old stack if still running: docker stack rm micro-app-24-6

- Run the new stack: docker stack deploy -c micro.yml micro-app-24-6

- Run docker service ls to get the correct service id for NGINX

- Watch the log file: docker service logs -f **nginx service** |& tee logs.txt

On locust:

- Change bias in locust script

- docker build -t locust/mytests .

- docker run --rm -d -e "LOCUST_OPTS=--no-web -c 500 -r 20 --run-time 1h" locust/mytests
