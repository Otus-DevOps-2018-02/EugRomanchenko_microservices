[![Build Status](https://travis-ci.org/Otus-DevOps-2018-02/EugRomanchenko_microservices.svg?branch=master)](https://travis-ci.org/Otus-DevOps-2018-02/EugRomanchenko_microservices)
# EugRomanchenko_microservices
EugRomanchenko microservices repository

## ДЗ № 13 Технология контейнеризации. Введение в Docker.

 - [x] Основное ДЗ
 - [x] Задание со *

### В процессе сделано
 - Установлены утилиты docker, docker-compose, docker-machine
 - Изучены основные команды для работы с контейнерами в docker
 - Записан вывод команты `docker image` в файл `docker-1.log`
 - Для задания со * записано сравнение вывода команды `docker inspect` для container-id и для image-id на основе которого был создан контейнер

### Как запустить проект
не применимо

### Как проверить работоспособность
не применимо

## ДЗ № 14 Docker контейнеры

 - [x] Основное ДЗ
 - [x] Задание со *

### В процессе сделано
 - Создан новые проект docker в GCP
 - Изменены настройки gcloud для нового проекта
 - Произведен запуск docker-machine в GCE
 - Локальный docker настроен для использования docker-machine
 - Повторены действия с docker namespaces в соответствии с demo
 - Создана структура в соответствии с которой производится docker build контейнера с работающим приложением
 - Добавлено firewall rule в GCE для доступа к порту :9292 нашего приложения с помощью gcloud
 - Проивезеда регистрация в Docker Hub
 - Созданный на предыдущем этапе docker контейнер запушен в Docker Hub
 - Для задания со * создан прототип в docker-monolith/infra в соответствии с которым производится настройка инфраструктуры в GCE (terraforn), подготоавливается Golden Image с настроеным Docker (Ansible + Packer), создан Ansible Playbook для deploy Docker container from Docker Hub
