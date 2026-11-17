# Практическая работа №7. Docker basics

## Цель работы
Собрать собственный Docker-образ на базе веб-сервера **Nginx**, отдающий статическую HTML-страницу, настроить проброс порта `54321:80` и автоматизировать сборку и запуск контейнера с помощью shell-скрипта.

## Структура проекта

```text
devops6docker/
├── deploy.sh
└── nginx/
    ├── dockerfile
    ├── index.html
    └── nginx-conf/
        └── nginx.conf
```

## Исходные файлы и конфигурация

### 1. Скрипт сборки и запуска (`deploy.sh`)
Скрипт останавливает и удаляет предыдущий контейнер, собирает образ `devops/nginx-server` и запускает новый контейнер в фоновом режиме с пробросом порта.

> **<img width="705" height="418" alt="image" src="https://github.com/user-attachments/assets/77dd03fe-1ac5-43a4-84d1-bcf0d08f2a0d" />**


### 2. Dockerfile (`nginx/dockerfile`)
Инструкция для сборки образа на базе официального `nginx`: копирование HTML-страницы и конфигурации, проверка синтаксиса `nginx -t`.

> **<img width="990" height="203" alt="image" src="https://github.com/user-attachments/assets/5fbd4bd4-8a3c-4944-99b5-4484896c15d5" />**


### 3. Конфигурация Nginx (`nginx/nginx-conf/nginx.conf`) и страница (`nginx/index.html`)

> **<img width="948" height="356" alt="image" src="https://github.com/user-attachments/assets/b3131555-92eb-4d7c-ad6b-6356655333cb" />**
> **<img width="1008" height="311" alt="image" src="https://github.com/user-attachments/assets/0cfdbcb3-1555-4401-a1e0-2427cceb7fd7" />**


## Запуск и проверка работоспособности

### Выполнение скрипта `./deploy.sh` и проверка статуса контейнера (`docker ps -a`)

> **<img width="1683" height="880" alt="image" src="https://github.com/user-attachments/assets/8568d40a-aff5-46fa-9d8b-3764de0fa104" />**
> **<img width="1604" height="897" alt="image" src="https://github.com/user-attachments/assets/70d44374-1b35-4ba5-be85-20cc022520bd" />**


### Проверка доступности веб-сервера (`curl` / браузер) и логов (`docker logs`)

> **<img width="1014" height="581" alt="image" src="https://github.com/user-attachments/assets/be81c0ea-42a6-45b0-99fc-dba671c5bfcf" />**
> **<img width="1260" height="1046" alt="image" src="https://github.com/user-attachments/assets/5af39b03-9c6b-4ed8-b087-886a97e8a890" />**

## Вывод
В ходе выполнения практической работы был собран собственный Docker-образ с веб-сервером Nginx, настроен проброс порта `54321` для доступа к контейнеру извне и написан bash-скрипт для автоматического развёртывания.
