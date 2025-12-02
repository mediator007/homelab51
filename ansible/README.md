# Плейбук для раскатки софта на homelab сервер

## Запуск playbook
- Выбрать используемый образ, например `cytopia/ansible:latest`
- Копировать ssh ключ в homelab/ansible/ssh  
- Выполнить команду из текущей директории:
```sh
docker run -it --rm \
  -v $(pwd):/work \
  -v $(pwd)/ssh/id_homelab:/ssh/id_homelab:ro \
  cytopia/ansible:latest \
  bash
```
- В контейнере:  
```sh
cd /work

# Проверяем связь с homelab
ansible homelab -m ping

# Запуск плейбука
ansible-playbook playbooks/<playbook>.yaml
```


## Требования для таргет хоста (homelab)
- Установить python3  

```sh
sudo apt install -y python3
```  




