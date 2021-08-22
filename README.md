# Granulate Devops task

- attached here the yml files user to deploy the resoucres in the web server with the steps I've done
# steps to run:
- ssh -i "exercise.pem" ubuntu@3.90.25.97
- Install apache web server - sudo docker run -d -p 8080:80 httpd
- Created a docker-compse yml file that contains kibana, elk and filebit
- start docker compose : sudo docker-compose up -d
- As sanity check u can do the following : curl -X GET "localhost:9200/_cat/nodes?v=true&pretty"
- Created a tunnel to my local machine to the services:
 1. ssh -L 9200:127.0.0.1:9200 -N -f -i "exercise.pem" ubuntu@3.90.25.97
 2. ssh -L 8080:127.0.0.1:80 -N -f -i "exercise.pem" ubuntu@3.90.25.97
 3. ssh -L 5601:127.0.0.1:5601 -N -f -i "exercise.pem" ubuntu@3.90.25.97
- u can follow the logs of filebit each time we refresh apache webserver at localhost:8080 with the following comman sudo docker logs filebit --follow
- accessed kibana through http://localhost:5601/app/kibana#/home?_g=() and discoverd the index
