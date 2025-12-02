SSH_KEY=ssh/id_homelab

PROJECT_DIR=$(shell pwd)

ANSIBLE_IMAGE=homelab-ansible:latest

INVENTORY=inventory.ini

.PHONY: build ping

build:
	@echo "Собираем Docker образ ansible-ssh:latest..."
	docker build -t $(ANSIBLE_IMAGE) .

ping: build
	@mkdir -p $(PROJECT_DIR)/ssh
	@echo "Проверка связи с homelab через Ansible..."
	docker run --rm \
		-v $(PROJECT_DIR):/work \
		-v $(PROJECT_DIR)/$(SSH_KEY):/ssh/id_homelab:ro \
		$(ANSIBLE_IMAGE) \
		ansible homelab -i /work/$(INVENTORY) -m ping -u viktor --private-key /ssh/id_homelab


