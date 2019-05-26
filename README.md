# Microservices - Docker, Flask, React

[![Build Status](https://travis-ci.com/huarngpa/microservices-flask-react.svg?branch=master)](https://travis-ci.com/huarngpa/microservices-flask-react)

## Part 1: Docker and Flask

### Docker and Docker-Compose Commands
```sh
docker-compose -f docker-compose.yml up -d --build # when new deps
docker-compose -f docker-compose-prod.yml up -d # should auto-update?
docker-compose -f docker-compose.yml down
docker-compose -f docker-compose.yml exec users python manage.py test
docker-compose -f docker-compose.yml exec users python manage.py shell
docker-compose -f docker-compose.yml exec users python manage.py recreate_db
docker-compose -f docker-compose.yml exec users python manage.py seed_db
docker-compose -f docker-compose.yml exec users-db psql -U postgres
docker image rm $(docker images -f "dangling=true" -q)
docker-compose -f docker-compose-prod.yml exec users env
```

### IAM
[IAM sign-in](https://huarngpa.signin.aws.amazon.com/console)

### Docker-Machine Commands
```sh
docker-machine ls # list machines
docker-machine create --driver amazonec2 testdriven-prod
docker-machine env testdriven-prod
docker-machine ssh testdriven-prod
eval $(docker-machine env testdriven-prod) # change to target machine
eval $(docker-machine env --unset) # reverts
docker info # which machine
docker-machine ip testdriven-prod
```

## Part 2: Code Coverage and React

### Docker and Docker-Compose Commands
```sh
docker-compose -f docker-compose.yml exec users python manage.py cov
docker-compose -f docker-compose.yml exec users flake8 project
```

### Environment Variables
You will need to supply this one-off environment variable for dev and production builds
```
export REACT_APP_USERS_SERVICE_URL=http://localhost # local
export REACT_APP_USERS_SERVICE_URL=http://<public-ip> # prod
```

### React Commands
```sh
npm start
npm test
```

## Part 3: Flask Migrate and Bcrypt
```sh
docker-compose exec users python manage.py db init
docker-compose exec users python manage.py db migrate # database changes
docker-compose exec users python manage.py db upgrade # apply changes
```
