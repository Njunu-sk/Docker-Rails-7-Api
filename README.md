# README

Authenticate your Rails Api

 /signup

 `curl -X POST --data "name=test"  --data "email=test@test.com"  --data "password=password"  --data "password_confirmation=password" http://localhost:3000/signup`

/auth/login

`curl -X POST --data "email=test@test.com"  --data "password=password" http://localhost:3000/auth/login`



