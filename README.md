# Commands

## Part 1: Docker and Flask

### Docker and Docker-Compose Commands
```sh
docker-compose -f docker-compose-dev.yml up -d --build # when new deps
docker-compose -f docker-compose-prod.yml up -d # should auto-update?
docker-compose -f docker-compose-dev.yml down
docker-compose -f docker-compose-dev.yml exec users python manage.py test
docker-compose -f docker-compose-dev.yml exec users python manage.py shell
docker-compose -f docker-compose-dev.yml exec users python manage.py recreate_db
docker-compose -f docker-compose-dev.yml exec users python manage.py seed_db
docker-compose -f docker-compose-dev.yml exec users-db psql -U postgres
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
docker-compose -f docker-compose-dev.yml exec users python manage.py cov
docker-compose -f docker-compose-dev.yml exec users flake8 project
```
