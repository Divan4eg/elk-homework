Домашнее задание к занятию «ELK. Первушин Дмитрий»

### Задание 1. Elasticsearch
Установите и запустите Elasticsearch, после чего поменяйте параметр cluster_name на случайный.

Приведите скриншот команды 'curl -X GET 'localhost:9200/_cluster/health?pretty', сделанной на сервере с установленным Elasticsearch. Где будет виден нестандартный cluster_name.

### Решение 1

```
version: '3.9'

services:
  elasticsearch:
    image: elasticsearch:9.1.3
    container_name: elasticsearch
    ports:
      - 9200:9200
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
      - cluster.name=pervushin_cluster
``` 

![Решение1](https://github.com/Divan4eg/elk-homework/blob/main/img/1.png)

### Задание 2. Kibana
Установите и запустите Kibana.

Приведите скриншот интерфейса Kibana на странице http://<ip вашего сервера>:5601/app/dev_tools#/console, где будет выполнен запрос GET /_cluster/health?pretty.

### Решение 2

```
  kibana:
    image: kibana:9.1.3
    container_name: kibana
    ports:
      - 5601:5601
    depends_on:
      - elasticsearch
``` 

![Решение2](https://github.com/Divan4eg/elk-homework/blob/main/img/2.png)

### Задание 3. Logstash
Установите и запустите Logstash и Nginx. С помощью Logstash отправьте access-лог Nginx в Elasticsearch.

Приведите скриншот интерфейса Kibana, на котором видны логи Nginx.

### Решение 3

![Решение3](https://github.com/Divan4eg/elk-homework/blob/main/img/3.png)

### Задание 4. Filebeat.
Установите и запустите Filebeat. Переключите поставку логов Nginx с Logstash на Filebeat.

Приведите скриншот интерфейса Kibana, на котором видны логи Nginx, которые были отправлены через Filebeat.

### Решение 4

### Все 3 data-view, созданные по заданиям 3-4
![Решение4](https://github.com/Divan4eg/elk-homework/blob/main/img/4.png)


### Сам просмотр логов доступа и ошибок Nginx
![Решение4](https://github.com/Divan4eg/elk-homework/blob/main/img/5.png)
![Решение4](https://github.com/Divan4eg/elk-homework/blob/main/img/6.png)
