DOCKER_COMPOSE = docker compose
PODMAN = podman

IMAGE = memcached
CONTAINER_NAME = podman_memcached

down:
	$(DOCKER_COMPOSE) down --remove-orphans

up:
	$(DOCKER_COMPOSE) up --force-recreate --build -d

restart: down up

bash:
	$(DOCKER_COMPOSE) exec memcached bash

ps:
	$(DOCKER_COMPOSE) ps

logs:
	$(DOCKER_COMPOSE) logs

podman_down:
	$(PODMAN) stop $(CONTAINER_NAME)

podman_up:
	$(PODMAN) run -d --rm --name $(CONTAINER_NAME) -p 11211:11211 $(IMAGE)

podman_restart: podman_down podman_up

podman_bash:
	$(PODMAN) exec -ti $(CONTAINER_NAME) bash

podman_ps:
	$(PODMAN) ps

podman_logs:
	$(PODMAN) logs $(CONTAINER_NAME)
