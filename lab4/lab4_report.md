University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)  
Year: 2024/2025  
Group: K4111c  
Author: Iusupova Edna Eduardovna  
Lab: Lab4  
Date of create: 07.12.2024  
Date of finished:   

## Лабораторная работа №4 "Сети связи в Minikube, CNI и CoreDNS"  
#### Описание  
Это последняя лабораторная работа в которой вы познакомитесь с сетями связи в Minikube. Особенность Kubernetes заключается в том, что у него одновременно работают underlay и overlay сети, а управление может быть организованно различными CNI.  

#### Цель работы  
Познакомиться с CNI Calico и функцией IPAM Plugin, изучить особенности работы CNI и CoreDNS. 

#### Выполнение работы
##### Шаг 1. Запустить minikube с плагином CNI=calico и режимом работы Multi-Node Clusters, развернуть 2 ноды.

Запуск кластера с 2 нодами и использованием плагина calico
`minikube start --driver=docker --network-plugin=cni --cni=calico -p=multinode --nodes 2`

  ``  
  set HTTP_PROXY=http://<proxy hostname:port>
set HTTPS_PROXY=https://<proxy hostname:port>
set NO_PROXY=localhost,127.0.0.1,10.96.0.0/12,192.168.59.0/24,192.168.49.0/24,192.168.39.0/24

minikube start



##### Шаг 2. Проверить работу CNI плагина Calico и количество нод.

Проверка наличия 2 нод
`minikube kubectl get no`



##### Шаг 3. Проверить работу Calico с помощью функции IPAM Plugin.

`minikube service frontend-service`

##### Шаг 4. Проверить режим IPAM для запущеных ранее нод указать label по признаку стойки или географического расположения (на ваш выбор).
##### Шаг 5. Разработать манифест для Calico который бы на основе ранее указанных меток назначал бы IP адреса "подам" исходя из пулов IP адресов которые вы указали в манифесте.

##### Шаг 6. Создать deployment с 2 репликами контейнера ifilyaninitmo/itdt-contained-frontend:master и передать переменные в эти реплики: REACT_APP_USERNAME, REACT_APP_COMPANY_NAME.

##### Шаг 7. Создать сервис, через который будет доступ на эти "поды". Выбор типа сервиса остается на ваше усмотрение.

##### Шаг 8. Запустить в minikube режим проброса портов и подключитесь к контейнерам через веб браузер.

##### Шаг 9. Проверить на странице в веб браузере переменные Container name и Container IP. 
Изменяются ли они? Если да то почему?

##### Шаг 10. Используя kubectl exec зайти в любой "под" и попинговать "поды" используя FQDN имя соседенего "пода".