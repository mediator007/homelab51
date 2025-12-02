# Путь к приватному ключу внутри проекта
SSH_KEY=ssh/id_homelab

# Путь к директории проекта (текущая)
PROJECT_DIR=$(shell pwd)

# Docker образ с Ansible
ANSIBLE_IMAGE=cytopia/ansible:latest

# Inventory для Ansible
INVENTORY=inventory.ini

.PHONY: ping

ping:
	@echo "Проверка связи с homelab через Ansible"
	docker run --rm \
		-v $(PROJECT_DIR):/work \
		-v $(PROJECT_DIR)/$(SSH_KEY):/$(SSH_KEY):ro \
		$(ANSIBLE_IMAGE) \
		ansible homelab -i /work/$(INVENTORY) -m ping -u viktor --private-key /$(SSH_KEY)


