# Плейбук для раскатки софта на homelab сервер

## Запуск playbook
- Выбрать используемый образ, например `cytopia/ansible:latest`  
- Выполнить команду из текущей директории:  
```sh
mkdir -p ssh && \
docker run -it --rm \
  -v $(pwd):/work \
  -v $(pwd)/ssh/id_homelabhomelab51_id_rsa.private:/ssh/homelab51_id_rsa.private:ro \
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




