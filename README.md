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

## ДЗ № 15

 - [x] Основное ДЗ
 - [x] Задание со *
 - [x] Задание с **

### В процессе сделано
 - Наше приложение разбито на три компонента (ui, post, comment)
 - Созданы соответствующие Dockerfile для каждого компонента
 - Оптимизированы Dockerfile
 - Использован Docker linter [hadolint](https://github.com/hadolint/hadolint)
 - Запущены docker контейрены с использование network bridge и сетевых алиасов для взаимодействия контейнеров друг с другом
 - Для задания со * был произведен запуск контейнеров с другими сетевыми алиасами без пересборки образов с использованием передачи переменных через опцию `--env` при docker run
 - Произведена оптимизация размера получающегося docker image для контейнера ui путём оптимизации Dockerfile
 - Произведена оптимизация размера получающегося docker image для контейнера ui путём перехода замены ubuntu:16.04 на более легковесный alpine:3.7
 - Для задания со ** в GitHub Pull Request-е были сделаны предположения по возможностям дальнейшего уменьшения размера docker images контейнера ui
 - С целью сохранения ранее созданных постов в нашем приложении, был настроен и подключен к контейнеру с MongoDB docker volume
