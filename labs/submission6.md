## Запуск Docker

# Команды

Команда `docker ps -a` вывела
```
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

то есть ничего.


После установки ubuntu я запустил новую команду: ( звучит так, как будто писал ИИ, но нет)) ) `docker images ubuntu`

```
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
ubuntu       latest    bbdabce66f1b   4 weeks ago   78.1MB
```

Команды внутри ubuntu:

```
root@237379f6848e:/# cat /etc/os-release
PRETTY_NAME="Ubuntu 24.04.4 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.4 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

root@237379f6848e:/# ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   4588  3968 pts/0    Ss   09:49   0:00 /bin/bash
root        13  0.0  0.0   7888  4096 pts/0    R+   09:52   0:00 ps aux

root@237379f6848e:/# exit
exit
```

Я создал файл .tar:

```
osman@MacBook-Pro-Osman ~ % docker save -o ubuntu_image.tar ubuntu:latest
osman@MacBook-Pro-Osman ~ % ls -lh ubuntu_image.tar
-rw-------@ 1 osman  staff    77M 12 мар 12:53 ubuntu_image.tar
```

В нем сохранено все, что нужно для запуска Ubuntu. То есть просто создается копия образа Ubuntu.

Он весит чуть меньше, чем исходный образ (77M < 78.1M)

Ошибка при попытке удаления:
```
Error response from daemon: conflict: unable to remove repository reference "ubuntu:latest" (must force) - container 237379f6848e is using its referenced image bbdabce66f1b
```

Она возникает из-за того, что контейнер не может существовать без образа. Если удалить образ, возникнет ошибка с контейнером, поэтому Docker требует сначала удалить контейнер, чтобы на образ никто не ссылался. После этого удаление произойдет без ошибок.

В конце концов удаление прошло успешно:

```
osman@MacBook-Pro-Osman ~ % docker rm ubuntu_container
ubuntu_container
osman@MacBook-Pro-Osman ~ % docker rmi ubuntu:latest
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:d1e2e92c075e5ca139d51a140fff46f84315c0fdce203eab2807c7e495eff4f9
Deleted: sha256:bbdabce66f1b7dde0c081a6b4536d837cd81dd322dd8c99edd68860baf3b2db3
Deleted: sha256:efafae78d70c98626c521c246827389128e7d7ea442db31bc433934647f0c791
```


# Nginx

Welcome page:
```html
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, nginx is successfully installed and working.
Further configuration is required for the web server, reverse proxy, 
API gateway, load balancer, content cache, or other features.</p>

<p>For online documentation and support please refer to
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional 
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

Содержимое моего html файла:

```html
<html>
<head>
<title>The best</title>
</head>
<body>
<h1>website</h1>
</body>
</html>
```

вот, что дала команда `curl`:

```html
<html>
<head>
<title>The best</title>
</head>
<body>
<h1>website</h1>
</body>
</html>% 
```

Вот, что вывела команда `docker diff my_website_container`:

```
C /run
C /run/nginx.pid
C /etc
C /etc/nginx
C /etc/nginx/conf.d
C /etc/nginx/conf.d/default.conf
```

Никакие файлы не создавались и не удалялись, просто изменялись конфигурационные файлы.

## Преимущества и недостатки `docker commit` и `Dockerfile`

`docker commit` удобен тем, что можно в системе все настроить и сразу же сделать слепок. Однако нет никакой истории изменений (ввод команд), файл может весить много.

`Dockerfile` удобен тем, что содержит в себе инструкцию по созданию контейнера в виде небольшого файлика. Неудобство может быть разве что, если долго в первый раз будут загружаться файлы (ну и то, что нужно знать синтаксис).


# Сети

## Вывод ping

```
PING container2 (172.18.0.3): 56 data bytes
64 bytes from 172.18.0.3: seq=0 ttl=64 time=0.080 ms
64 bytes from 172.18.0.3: seq=1 ttl=64 time=0.116 ms
64 bytes from 172.18.0.3: seq=2 ttl=64 time=0.097 ms

--- container2 ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 0.080/0.097/0.116 ms
```

## Вывод `docker network inspect lab_network`

```
[
    {
        "Name": "lab_network",
        "Id": "b2e67d92d336e4a75a816bdee3b1dc06947a6ecc2dceecd8b40dcebf26c71c61",
        "Created": "2026-03-12T10:34:05.872671305Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.18.0.0/16",
                    "Gateway": "172.18.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "9b228ed6b2b1f72d9760530d5077a82456cd3cb569e49de07d1d9a7b44b108c8": {
                "Name": "container2",
                "EndpointID": "777d6bfb5db0183094d34a991e9e62a485d29424de86824a358a014ceb9490e8",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            },
            "acf9d576ece1077ffe2323aac8bd9b702530d8572081ede3330c50586a923445": {
                "Name": "container1",
                "EndpointID": "9d54a87fc8184ddb0d065f430b5f3ffd53ff928c1370e18ec57e4aba2ce778d4",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]
```

## DNS resolution

```
Server:		127.0.0.11
Address:	127.0.0.11:53

Non-authoritative answer:

Non-authoritative answer:
Name:	container2
Address: 172.18.0.3
```

## Анализ и сравнение

Когда пользователь создает пользовательскую сеть, запускается dns-сервер. Когда запускается контейнер с флагом `--name` или `--network-alias`, docker запоминает его имя и ip-адрес. Обращение второго контейнера к первому осуществляется за счет встроенного dns-сервера.

Пользовательская сеть безопаснее, потому что изолирована от необщающихся контейнеров. В ней можно обращаться по именам, а не по ip-адресам, а значит что если у контейнера поменялся ip-адрес, а имя нет, то это не проблема.

# Volumes

## Custom HTML

вот содержимое:

```
<html><body><h1>Persistent Data</h1></body></html>
```

## Восстановление

Уничтожен контейнер, но сохранен файл:
```
osman@MacBook-Pro-Osman labs % docker stop web && docker rm web
web
web
osman@MacBook-Pro-Osman labs % docker run -d -p 80:80 -v app_data:/usr/share/nginx/html --name web_new nginx
38fc04fe6aa7a62fe44612b58d5bf14c06c5147fb045357435d3e96ff08e846e
osman@MacBook-Pro-Osman labs % curl http://localhost
<html><body><h1>Persistent Data</h1></body></html>%      
```

## Volume inspection

```
[
    {
        "CreatedAt": "2026-03-12T10:49:16Z",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/app_data/_data",
        "Name": "app_data",
        "Options": null,
        "Scope": "local"
    }
]
```

## Ответы на вопросы

Важно сохранять данные, потому что они могут быть важны, и при удалении контейнера они удалятся (если не создать volume). Например, если нужно обновить версию nginx.

Container Storage хранит данные в контейнере, Volumes в выделенной для этого папке, Bind Mounts может храниться в любой папке на компе пользователя.
