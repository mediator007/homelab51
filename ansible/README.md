# Плейбук для раскатки софта на homelab сервер

## Запуск playbook
- Скопировать ssh ключ для доступа к homelab в директорию по пути  homelab/ansible/secrets/id_homelab  
- Записать пароль sudo для homelab в homelab/ansible/secrets/become  
- Запустить make target с необходимым плейбуком


## Требования для таргет хоста (homelab)
- Установить python3  

```sh
sudo apt install -y python3
```  




