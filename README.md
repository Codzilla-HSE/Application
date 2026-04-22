# nginx

## Зависимости

Для работы понадобится установленный `nginx`. 
* **Ubuntu/Debian:** `sudo apt install nginx`
* **macOS:** `brew install nginx`

> **Важно:** Убедитесь, что системный сервис nginx (если он запустился после установки) остановлен, чтобы он не занимал 80-й порт:  
> `sudo lsof -i :80` (чтобы узнать занимает или нет)
> `sudo systemctl stop nginx` (Linux) или `brew services stop nginx` (macOS).

## Как запустить локально

1. Перейдите в папку с конфигурацией:
   ```bash
   cd infra/nginx
2. Запустите Nginx в привязанном к терминалу режиме (чтобы видеть ошибки и легко останавливать через Ctrl+C):
    ```bash
    sudo nginx -p . -c nginx.conf -g "daemon off;"
    Сервер будет доступен по адресу http://localhost
3. Для проверки синтаксиса локально:
    ```bash
    sudo nginx -t -p . -c nginx.conf
    ```
    Вы должны увидеть:
    ```bash
    nginx: the configuration file ./nginx.conf syntax is ok
    nginx: configuration file ./nginx.conf test is successful

4. Если вы запустили его в фоновом режиме (без daemon off;), остановить его можно командой из папки infra/nginx:
    ```bash
    sudo nginx -p . -c nginx.conf -s stop