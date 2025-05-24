# Выбор и настройка мониторинга в системе

## Мотивация

 * С помощью сбора метрик можно быстрее выявлять узкие места и за счёт этого своевременнее реагировать на инциденты;
 * Как следствие это может улучшить пользовательский опыт;
 * Так же мониторинг позволяет выявлять нагрузку на разные части системы, и на этой основе можно под задачи использовать разное оборудование, что снизит расходы на инфраструктуру;

## Выбор подхода к мониторингу

 * Для MES важно мониторить нагрузку на систему, поэтому подойдут four golden signals или USE
 * Для `CRM` и `Internet shop` можно использовать `RED`-подход
 * Базы данных и очереди сообщений - `USE`.

## Метрики

### MES
 * Size of S3 storage
 * Number of requests (RPS) for MES API - нагрузка
 * Number of requests (RPS) per user for MES API - нагрузка 
 * Number of HTTP 200 for MES API - нагрузка
 * Number of HTTP 500 for MES API - нагрузка, ошибки
 * Number of simultanious sessions for MES API - нагрузка

### CRM

* Number of requests (RPS) for CRM API - нагрузка
* Number of requests (RPS) per user for CRM API - нагрузка
* Number of HTTP 200 for CRM API - нагрузка
* Number of HTTP 500 for CRM API - нагрузка, ошибки
* Number of simultanious sessions for CRM API - нагрузка

### Internet shop
 * Number of requests (RPS) for internet shop API - нагрузка
 * Number of requests (RPS) per user for internet shop API - нагрузка
 * Memory Utilisation for shop db instance - насыщение
 * Number of HTTP 200 for shop API - нагрузка
 * Number of HTTP 500 for shop API - нагрузка, ошибки
 * Number of simultanious sessions for shop API - нагрузка  
 
### Брокер сообщений
 * Number of dead-letter-exchange letters in RabbitMQ - мониторинг ошибок
 * Number of message in flight in RabbitMQ - мониторинг нагрузки

### Postgresql
 * Memory Utilisation for MES db instance - насыщение
 * Memory Utilisation for shop db instance - насыщение
 * Number of connections for shop db instance - нагрузка, слишком большое значение может указывать на ошибки, например клиенты не закрывают соединения с БД 
 * Number of connections for MES db instance
 * Size of shop db instance - насыщение, позволяет вовремя среагировать, и, например, разбить БД на шарды
 * Size of MES db instance

## План действий

 * Развернуть и настроить Prometheus;
 * Реализовать в сервисах передачу метрик;
 * Развернуть Grafana, настроить её для получения метрик с Prometheus;
 * Добавить в Grafana дашборды для визуализации метрик;
 * Настроить алерты в grafana.

