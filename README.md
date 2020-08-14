# Sample project
## LAMP Stack with Docker Containers

### Requirements
 - Docker >= 18.03
 - docker-compose >= 1.17
 - Git >= 1.8

### Repository Dependencies
- payment-service
- attendance-service
- pa-app

### Installation
Copy the environment from example and configure it:
```sh
$ cp .env.example .env
```
Clone the associated projects and execute the commands:
```sh
$ docker-compose up -d
$ docker exec -it pa-app bash
$ npm install
```
Enter in Lumen containers and configure the environments.
```sh
$ docker exec -it <project-name> bash
$ [...]
```

### Configuration
The first time it's necessary to add at the end of the "hosts" file: <br>
(for Windows OS open c:\Windows\System32\Drivers\etc\hosts with Administrator privileges)
```sh
127.0.0.1 attendance-service.local
127.0.0.1 payment-service.local
```
To run the React App execute the commands:
```sh
$ docker exec -it -d pa-app npm start
```

To rebuild Docker images:
```sh
$ docker-compose up -d --build
```

### Deploy
By default, the docker-compose will expose:
 * http://attendance-service.local/ - Attendance Service
 * http://payment-service.local/ - Payment Service
 * http://localhost:3000 - PA App

Verify the deployment by navigating in your preferred browser.

It's possible to verify and edit containers using command:
```sh
$ docker ps
$ docker exec -it <NAMES> bash
```

## Extra
### Custom Docker Images
Some containers are customized and the images are saved on Docker Hub or can be built with Dockerfile stored in the ".docker" folder.
The images stored on DockerHub are updated automatically by pushing the relative project saved on GitLab <br>
# mydocker-lamp
