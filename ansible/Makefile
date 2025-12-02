SSH_KEY=secrets/id_homelab

PROJECT_DIR=$(shell pwd)

ANSIBLE_IMAGE=homelab-ansible:latest

INVENTORY=inventory.ini

.PHONY: build ping

build:
	@echo "Собираем Docker образ ansible-ssh:latest..."
	docker build -t $(ANSIBLE_IMAGE) .

ping: build
	@echo "Проверка связи с homelab через Ansible..."
	docker run --rm \
		-v $(PROJECT_DIR):/work \
		-v $(PROJECT_DIR)/$(SSH_KEY):/secrets/id_homelab:ro \
		$(ANSIBLE_IMAGE) \
		ansible homelab -i /work/$(INVENTORY) -m ping -u viktor --private-key /secrets/id_homelab

docker:
	@echo "Накатываем Docker на homelab через Ansible"
	docker run --rm \
		-v $(PROJECT_DIR):/work \
		-v $(PROJECT_DIR)/secrets/id_homelab:/secrets/id_homelab:ro \
		homelab-ansible:latest \
		ansible-playbook /work/playbooks/docker.yaml -i /work/$(INVENTORY) -u viktor \
			--private-key /secrets/id_homelab \
			--become --become-password-file secrets/become
