# Concert App

## _An app api+frontend - integrated with firare microservices:keyrock,orion etc._

Microservice architecture front-end(svelte),api-server(node),orion,fiware idm(keyrock)

- Microservices
- pub/sub service to notify users on db changes.
- fiware idm(Keyrock) to manage authentication/authorization and user roles
- The whole project uses 3 databases 2 mongodb: 1 for pub/sub microservice 1 used by the app-express 1 MySQL used for user authentication through fiware-idm microservice.
- ✨Magic ✨

## Run Locally

- To run the application locally on your machine run: `docker-compose up` or even better run: `bash _bashScripts/cleanStart.sh` from the main directory.
- After that you have to go to http://localhost:5001/ get the oauth2 credentials and update "/app-express/.env" file.
- Credentials to get oauth2 credentials:
  - email: admin@test.com
  - password: 1234
- The first user you are going to create it's gonna be an admin too.

## Roles explanation

Users can have one or more roles.Each user gets role=user on creation.After that admin(s) can give him permissions to do more

- user:
  - user can do live search(key sensitive) with multiple filters.
  - add concerts to favorites and/or subscribe to them.
  - If he subscribes to them he will get notifications when some fields of the concert infos are changing(soldOut,startDate,stopDate).
  - This happens through the pub/sub microservice which triggers when changes happens on database side.
- admin: - Admin can see all the users,delete users, update their roles etc.
  -eventOrganizer: - Can create events and modify them.

## Watch the Demo online http://34.118.86.60/

- A Demo with dummy data may exist at: http://34.118.86.60/
- In case server has been paused you can ask me to resume it.

## Dummy data on online demo

> roles:eventOrganizers&user
> email: user<n>@gmail.com n=1,2
> password: password

> roles:user
> email: user<n>@gmail.com n=3,4
> password: password

> roles:user,admin
> email: admin@gmail.com
> password: password
