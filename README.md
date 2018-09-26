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

## ДЗ № 16 Docker: сети, docker-compose

 - [x] Основное ДЗ
 - [x] Задания со *

### В процессе сделано

 - Произведён запус контейнера joffotron/nginx с использованием следующих сетевых драйверов - none, host
 - Выполнено сравнение вывода команд `docker exec -ti net_test ifconfig` и `docker-machine ssh docker-host ifconfig` для обоих случаев
 - Настроена возможность просмотра существующих network namespace-ов 
 - Произведён запуск наших docker контейреров с использованием заранее созданной bridge-сети reddit 
 - Организована сетевая изоляция контейнера с ui от контейнера с DB путём создания двух отдельных bridge сетей
 - Опробован механизм подключения дополнительных сетевых интерфесов к запущенным docker контейнерам путём выполнения команд `docker network connect docker_bridge_name container_name`
 - Произведён осмотр настроек сетевого стека Linux в docker-machine, с помощью которого происходит взаимодействие docker контейнеров друг с другом и с внешним миром (механизмы виртуальных сетевых интерфейсов, бриджей, проброс сетевого трафика внутрь контейнеров с помощью iptables DNAT и Postrouting Masquerade)
 - Убедились что взаимодействие контейнеров с окружающим миром происходит с участием docker-proxy процесса
 - Установили утилиту docker-compose
 - Создали docker-compose.yml с описанием процесса сборки и запуска наших docker контейнеров
 - Произвели запуск наших микросервисов посредством `docker-compose up -d`
 - Параметризовали конфигурацию docker-compose.yml с использованием Enviromnent файла .env а также добавили возможность подключение к контейнерам нескольких сетевых компонент 
 - Изучили каким способом можно изменить название проекта при запуке Docker Compose. Это можно сделать указав название проекта после опции `-p` или же заданием переменной окружения `COMPOSE_PROJECT_NAME`
 - Создали дополнительный конфигурационный файл docker-compose.override.yml в соответствии с которым мы сможем изменять код наших микросерфисов без необходимости пересборки образов. А также включили опции дебага для приложений, работающих на ruby.

## ДЗ № 17 Gitlab CI. Построение процесса непрерывной интеграции

 - [x] Основное ДЗ
 - [x] Задание со *

### В процессе сделано

 - Произведена установка и настройка Gitlab CI с использованием варианта установки Docker-machine -> Docker-compose -> Gitlab CI CE Omnibus
 - Внутри Gitlab создан тестовая группа homework
 - Внутри Gitlab создан тестовый проект example в рамках группы homework
 - Настроен простой Gitlab Pipeline для прохождения тестов
 - Произведена настройка и регистрация Gitlab Runner-а
 - Тестовый репозиторий был добавлен в качестве Git remote к EugRomanchenko_microservices
 - Исходный код приложения Reddit был добавлен в тестовый репозиторий на Gitlab
 - Для него были изменены настройки Gitlab Pipeline-а для прохождения юнит теста
 - В рамках одного из заданий со * была настроена интеграция Gitlab со Slack для отправки нотификаций при любых действиях с тестовым репозиторием
 - Для автоматизации развертывания большого количества Gitlab Runner-ов предполагается написать простенький bash скрипт, который будет использовать возможность регистрации в неинтерактивном режиме (опция команды gitlab-runner register --non-interactive)

## ДЗ № 18 Устройство Gitlab CI. Непрерываня поставка

 - [x] Основное ДЗ
 - [x] Задание со *

### В процессе сделано

 - Создан новый проект в Gitlab CI `example2`
 - Для нового проекта включен gitlab runner
 - Существующий Gitlab CI Pipeline был расширен путём использования переменных окружения для каждой среды
 - Реализована возможность ручного запуска отдельных задач путём испольования директимы `when` со значением `manual`
 - С помощью директивы `only` добились того, что отдельные задачи не будут запущены без указания git tag-ов при заливке кода в репозиторий
 - Использованы Dynamic Environment
 - В рамках задания со * была реализована возможность создания сервера в GCE при пуше новой ветки в репозиторий а также его удаление при ручном нажатии на кнопку в соответствующем Pipeline

## ДЗ № 19 Введение в мониторинг. Системы мониторинга.

 - [x] Основное ДЗ
 - [x] Задание со *

### В процессе сделано

 - Созданы правила фаерволла в GCE для подключения к Prometheus и нашему приложению
 - С помощью docker-machine создан сервер в GCE на котором был развернут Docker образ Prometheus-а
 - Изучены основные элементы веб интерфейса Prometheus и базовые метрики
 - На основе базового Docker Hub образа Prometheus был собран свой с кастомным конфигом prometheus.yml
 - В prometheus.yml были объявлены задачи по сбору метрик с наших микросервисов
 - Были собраны Docker образа с нашими микросервисами с использованием скриптов docker_build.sh
 - Посредством созданного docker-compose.yml были залиты и запущены Docker контейнеры с настроенными микросервисами и приложением Prometheus
 - Произведен эксперимент эмулирующий проблемы с доступностью одного из микросервисов и изучением процесса дебага через мониторинг Prometheus
 - Настроен Node Exporter для сбора внутренних метрик DOcker контейнера на котором запущен Prometheus
 - В рамках одного из заданий со * был настроен MongoDB Exporter для сбора метрик и мониторинга базы данных Mongo DB
 - В рамках одного из заданий со * был настроен Blackbox мониторинг микросервисов (выявление случаев отдачи HTTP Code 2xx сервисами)
 - Ссылка на Docker Hub с образами - [Docker Hub Eugromanchenko](https://hub.docker.com/r/eugromanchenko/)

## ДЗ № 20 Мониторинг приложения и инфраструктуры

 - [x] Основное ДЗ
 - [x] Задание со *
 - [x] Задание с **

### В процессе сделано:

 - Составлены отдельные docker-compose файлы для microservice и инструментов мониторинга
 - Добавлено использование cAdvisor для просмотра метрик Docker контейнеров
 - Пересобрали Docker Image Prometheus
 - Изучили интерфейс cAdvisor и список метрик в нём
 - Установили Grafana с помощью docker-compose-monitoring.yml
 - Подключили к Grafana источник данных Prometheus
 - Загрузили с сайта [Grafana Dashboards](https://grafana.com/dashboards) Dashboard для мониторинга Docker контейнеров (сохранили как DockerMonitoring.json)
 - Произвели импорт полученного Dashboard в Grafana
 - Создали Dashborad с использованием функционала отдачи метрик Docker конейнерами с нашими microservices (сохранили как UI_Service_Monitoring.json)
 - Воспользовались возможностью отдачи нашими mircoservices бизнес метрик и построили на их основе отдельный Dashboard (сохранили как Business_logic_Monitoring.json)
 - Установили и настроили Alertmanager для Prometheus
 - Настроили отправку оповещений о проблемах в Slack канал #eugeny_romanchenko
 - Создали простой Alert Rule (cрабатывает в случае недоступности любого из компонент нашего приложения)
 - В качестве задания со * воспользовались экспериментальной функцией отдачи метрик Docker Daemon серверу Prometheus
 - В качестве задания с ** настроили автоматическую настройку Grafana Datasource (Prometheus) и подключение настроенных в ходе данного ДЗ Dashboards c использованием нового функционала provisioning появившегося в Grafana 5.0.0
 - Ссылка на Docker Hub с образами - [Docker Hub Eugromanchenko](https://hub.docker.com/r/eugromanchenko/)

## ДЗ № 21 Логирование и распределенная трассировка

 - [x] Основное ДЗ
 - [x] Задание со *
 - [x] Задание с ***

### В процессе сделано

 - Сформированы отдельные docker images на основе обновленного кода приложений с tag logging
 - Создан `docker-compose-logging.yml` для подготовки инфрастуктуры логирования на основе стэка EFK
 - Cформирован docker images Fluentd с кастомным конфигом fluent.com
 - Для сервисов post и ui настроена отправка логов в Fluentd
 - В Kibana был создан индекс `fluentd-*`
 - В мониторе Kibana были просмотрены получаемые логи с наших микросервисов
 - Настроен фильтр в Fluentd на основе json format
 - Для неструктурированных логов приложения ui был написан фильтр в Fluentd на основе использования регулярных выражений
 - Существующий фильтр был улучшес с использованием grok pattern
 - В рамках задания со * был написан второй grok pattern для окончательного разбора неструктурированных логов сервиса ui
 - В рамках задания с *** была произведена установка и подключение Zipkin для реализации  распределенной трассировки
 - В рамках задания с *** на основе поломанного кода приложения были собраны отдельные docker images с tag bugged
 - Произведен запуск сервисов на основе поломанного кода и произведен дебаг проблемы долгой загрузки Post-ов в web интерфейсе

## ДЗ № 22 Введение в Kubernetes

 - [x] Основное ДЗ

### В процессе сделано:

 - Созданы базовые конфиги для Deployment наших microservice в будущий Kubernetes Cluster
 - Пройден tutorial "Kubernetes The Hard Way" с целью изучения основных компонент и процессов при работе с Kubernetes
 - Произведен тестовый запус наших приложений в свежесозданном Kubernetes Cluster `kubectl apply kubernetes/reddit/*yml`

## ДЗ № 23 Kubernetes. Запуск кластера и приложения. Модель безопасности.

 - [x] Основное ДЗ

### В процессе сделано

 - Установлены инструменты kubectl и minikube
 - Созданы YAML конфиги для запуска микросервисов в локальном Kubernetes Cluster-е развёрнутом с помощью minikube
 - Создан Kubernetes Cluster в Google Cloud (GKE)
 - В GKE был произведен деплой наших микросервисов
 - Для GKE был включен Kubernetes Dashboard и были выданы права соответствующему Service Account-у

## ДЗ № 24 Kubernetes. Network. Storage.

 - [x] Основное ДЗ

### В процессе сделано:

 - Использован тип сервиса LoadBalancer
 - Включено и настроено использование Ingress контроллера для взаимодействия приложений внутри кластера с внешним миром
 - С помощью Ingress настроена балансировка на L-7 уровне (http)
 - Настроена TLS Termination (https)
 - Для задачи ограничения доступа к микросервису с DB был использован функционал Network Policy
 - Настроено использование Mongo DB различных типов Volume (Empty Dir, Persistent Disk. Persistent Volume, Storage Class)

## ДЗ № 25 CI/CD в Kubernetes

 - [x] Основное ДЗ

### В процессе сделано:

 - Установлен и сконфигурирован Helm в ранее созданном Google Kubernetes Cluster
 - Подготовлены и задеплоены Charts пакеты с приложениями comment, ui и post
 - При подготовке Charts были использваны возможности параметризации через template function
 - Для удобства управлениями зависимостями был создан общий Chart reddit
 - Произведен деплой Chart reddit
 - Был произведен запуск Gitlab CE с помощью Helm Chart
 - В Gitlab были созданы 4 отдельных публичных репозитория - ui, comment, post, reddit-deploy
 - Код приложений был перенесен в соответствующие репозитории
 - Для всех репозиториев были сформированы файлы gitlab-ci.yml для настройки соответствующих Pipeline для управления процессами CI/CD
