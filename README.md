# README

## Dockerize your Rails 7 Api in Dev.

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



