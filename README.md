# AQA-2.14_Netology-Home-Project

### Предварительная конфигурация ElasticSearch:

 #### 1. Настроить параметр {vm.max_map_count}:
 - $ screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty (press Enter) 
 - \# sysctl -w vm.max_map_count=262144
    
 #### 2. Задать права доступа к папке ElasticSearch c помощью команд:
 - $ mkdir -p data/elasticsearch
 - $ chmod g+rwx data/elasticsearch
 - $ chgrp 1000 data/elasticsearch
 
### Развернуть все контейнеры:
 - docker-compose -p reportportal up -d --force-recreate --build
 
### Удалить все контейнеры:
 - docker ps -a | grep "reportportal_" | awk '{print $1}' | xargs docker rm -f
 
### Запуск SUT: 
  - java -jar ./artifacts/app-card-delivery.jar -PassThru

### Запуск тестов: 
 - ./gradlew test
