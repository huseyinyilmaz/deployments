DOCKER_COMPOSE = docker-compose
DATA_DIR = data
LOGS_DIR = logs

.PHONY: help
help: ## This outputs help information.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

.PHONY: down
down: ## Takes down docker-compose configuration
	$(DOCKER_COMPOSE) down --remove-orphans

.PHONY: up
up: ## Starts docker-compose configuration
	$(DOCKER_COMPOSE) up --force-recreate --build -d

.PHONY: restart
restart: down up ## Restarts docker-compose configuration

.PHONY: shell
shell: ## starts a shell in container. 
	$(DOCKER_COMPOSE) exec memcached bash

.PHONY: ps
ps: ## Shows the status of running containers.
	$(DOCKER_COMPOSE) ps

.PHONY: logs
logs: ## Shows docker logs
	$(DOCKER_COMPOSE) logs

.PHONY: clean
clean: down ## Cleans up container volumes
	sudo rm -rf $(LOGS_DIR)
	sudo rm -rf $(DATA_DIR)

.PHONY: init
init: clean ## Initializes container volumes. (run this at least once before running the containers)
	mkdir $(LOGS_DIR)
	mkdir $(DATA_DIR)
	chmod a+rw $(LOGS_DIR)
	chmod a+rw $(DATA_DIR)
