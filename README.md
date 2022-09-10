# README

## Dockerize your Rails 7 Api.

### Development

`git@github.com:Njunu-sk/Docker-Rails-7-Api.git`

### Run docker image

`docker-compose up`

### Set up your database

`docker compose run --rm app bin/rails db:reset`

### Vefify container is up

`docker ps`

### Authenticate your Rails Api

- Check out the `signup` & `login` end - points

 # /signup

 `curl -X POST --data "name=test"  --data "email=test@test.com"  --data "password=password"  --data "password_confirmation=password" http://localhost:3000/signup`

# /auth/login

`curl -X POST --data "email=test@test.com"  --data "password=password" http://localhost:3000/auth/login`

### Production

- Create a Dockerfile for production image
`cp Dockerfile.dev Dockerfile.prod`

- Create a docker hub repo in Docker Hub

- Build our production image

 `docker build -f Dockerfile.prod -t username/authenticate-api:prod .`

- Login to Docker Hub account with the CLI

  `docker login`

- Push image to docker hub

  `docker push username/authenticate-api:prod`

## Note

- Set up `VirtualBox` to create virtual infrastructure on our local machine that can simulate a production env.

- Install `Docker Machine`

 `brew install docker-machine`

- Create a new virtual machine for running our app,

`docker-machine create --driver virtualbox local-vm-1`

- Verify creation if instance

  `docker-machine ls`

- SSH into instance

  `docker-machine ssh local-vm-1`

## Docker Swarm


- We turned our vanilla Docker instance into a single-node swarm cluster:

  `docker swarm init --advertise-addr <IP address of instance>`

  - Access ip address

  `docker-machine ls`

- Create a stackfile

  `cp docker-compose.yml docker-stack.yml`

- Rebuild image and push changes to Docker Hub

  `docker build -f Dockerfile.prod -t username/authenticate-api:prod .`

  `docker push username/authenticate-api:prod`

- Deploy to swarm

  `docker stack deploy -c docker-stack.yml authenticate-api`

- List services in the stack

  `docker stack services authenticate-api`

- Scaled up our web service by running multiple containers, utilizing
Swarm’s built-in load balancing:

  `docker service scale authenticate-api=<n>`

