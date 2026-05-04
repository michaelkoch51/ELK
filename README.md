# ELK
# Отчет по выполнению практического задания, студент: Михаил Кочнев
# Среда выполнения: macOS (M1 Apple Silicon) 
# Задание 1. Elasticsearch Цель: 
Установить и запустить Elasticsearch, изменить имя кластера. Выполнение: Elasticsearch версии 9.3.4 успешно установлен и запущен.      В конфигурационном файле config/elasticsearch.yml параметр cluster_name изменен на случайное значение: mihail-m1-cluster.
Скриншот №1: Вывод команды curl -X GET 'localhost:9200/_cluster/health?pretty', на котором виден статус кластера и нестандартное имя.

![Elasticsearch](https://github.com/user-attachments/assets/df351137-dadb-481d-b2e9-87ddbc767df0)  

# Задание 2. Kibana Цель: 
Установить и запустить Kibana, выполнил запрос через консоль Dev Tools. Выполнение: Kibana версии 9.3.4 установлена и настроена на подключение к локальному узлу Elasticsearch (http://localhost:9200). В интерфейсе Kibana успешно выполнен запрос к API кластера.
Скриншот №2: Интерфейс Kibana на странице Dev Tools, отображающий результат запроса GET /_cluster/health?pretty.

![Kibana](https://github.com/user-attachments/assets/eca7c2a4-c489-4f61-89e9-9d5fe0458ba5)  

# Задание 3. Logstash Цель:
Установить Logstash и Nginx, отправить access-логи Nginx в Elasticsearch через Logstash. Выполнение: Установлен веб-сервер Nginx через Homebrew. Настроен конфигурационный файл Logstash для чтения логов по пути /opt/homebrew/var/log/nginx/access.log.Создан индекс logstash-nginx, данные успешно проиндексированы и отображены в Kibana.
Скриншот №3: Раздел Discover в Kibana, в котором видны записи логов Nginx, переданные через Logstash.

![Logstash](https://github.com/user-attachments/assets/88065963-539d-4f91-8789-50dfaf921f41)  

# Задание 4. Filebeat Цель: 
Установить Filebeat, переключить поставку логов с Logstash на Filebeat. Выполнение: Установлен и настроен Filebeat. Активирован модуль nginx для автоматического сбора логов. Логи успешно перенаправлены напрямую в Elasticsearch в индекс filebeat-task.В Kibana создано представление данных (Data View) для визуализации полученных логов. 
Скриншот №4: Интерфейс Kibana с логами Nginx, где в поле agent.type указано значение filebeat. Результат: Все компоненты стека ELK настроены и интегрированы. Потоки данных от веб-сервера Nginx успешно визуализированы двумя различными способами.

![Filebeat](https://github.com/user-attachments/assets/474ba99b-c8fb-4f61-b6cc-83eedb2c65e4)
