DOCKER_COMPOSE = docker-compose

down:
	$(DOCKER_COMPOSE) down --remove-orphans

up:
	$(DOCKER_COMPOSE) up --force-recreate --build -d

restart: down up

bash:
	$(DOCKER_COMPOSE) exec redis bash

ps:
	$(DOCKER_COMPOSE) ps

logs:
	$(DOCKER_COMPOSE) logs
