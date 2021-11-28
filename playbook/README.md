# About playbook

## Состав

* Playbook состоит из нескольких `play`:
   - Инсталляция ElasticSearch
   - Инсталляция Kibana
   - Инсталляция Filebeat
-------------------------------------

## Задачи в каждом из `play`:

* `Install Elasticsearch`:
  * Разделен на задачи:
    * Перезагрузка сервиса, в случае обращения задачи к нему (handlers)
    * Скачивание пакета `rpm` с `elasticsearch`
    * Инсталляция `elasticsearch` с `yam`
    * Конфигурация `elasticsearch` с передачей файла [elasticsearch.yml.j2](templates/elasticsearch.yml.j2) и рестарт сервиса по завершению (notify)

-----------------
* `Install Kibana`:
  * Разделен на задачи:
    * Перезагрузка сервиса, в случае обращения задачи к нему (handlers)
    * Скачивание пакета `rpm` с `kibana`
    * Инсталляция `kibana` с `yam`
    * Конфигурация `kibana` с передачей файла [kibana.yml.j2](templates/kibana.yml.j2)  и рестарт сервиса по завершению (notify)

-----------------
* `Install Filebeat`:
  * Разделен на задачи:
    * Скачивание пакета `rpm` с `filebeat`
    * Конфигурация `filebeat` с передачей файла [filebeat.yml.j2](templates/filebeat.yml.j2)
    * Установка модуля `system`
    * Установка `dashboard`