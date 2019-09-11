# app_manager
Contains docker-compose file for micro app (bbk project)

Command to listen for logs:

Create log text file

Edit yml file to select the right number of containers

Remove the old stack if still running: docker stack rm micro-app-24-6

Run the new stack: docker stack deploy -c micro.yml micro-app-24-6

Run docker service ls to get the correct service id for NGINX

Watch the log file: docker service logs -f **nginx service** |& tee logs.txt

On locust:

Change bias in locust script

docker build -t locust/mytests .

docker run --rm -d -e "LOCUST_OPTS=--no-web -c 500 -r 20 --run-time 1h" locust/mytests
