# Logstash_TechJournal: Парсинг технологического журнала 1С (ТЖ <- logstash -> elastic) 

# Назначение
Данный проект создан для простой настройки экспорта технологического журнала в системы анализа и мониторинга.


# Возможности
Logstash_TechJournal - это настроенная конфигурация Logstash [настроенная конфигурация Logstash](./logstash/pipeline/logstash-tj.config) для экспорта в elastic.

Поддерживаемые поля и их псевдонимы после слоя фильтрации:

| Источник    | Поле | Комментарий |
| -------- | ------- |------ |
| -  | duration_msec    |время выполнения события стандартное |
| - | duration_sec     |время выполнения события в секундах |
| -    | duration_minutes    | время выполнения события в минутах |
| -    | @timestamp    | дата события собирается из имени файла и времени событя ТЖ |
| -    | event    | событие технологического журнала |
| -    | nesting_level    | уровень вложенности события технологическго журнала |
| process=    | process    | ------ |
| p:processName=    | pprocessname    | ------ |
| t:applicationName    | application    | ------ |
| t:clientID=    | clientid    | ------ |
| Usr=    | username    | ------ |
| DataBase=    | infobase    | ------ |
| SThread=    | osthread    | ------ |
| SessionID=    | sessionid    | ------ |
| Regions=    | region    | ------ |
| Locks=    | locks    | ------ |
| WaitConnections=    | waitconnections    | ------ |
| Context=    | context    | ------ |
| Descr=    | description    | ------ |
| Sdbl=    | sdbl    | ------ |

Предоставляет возможность чтения файлов ТЖ, их парсинг, преобразование и дальнейший экспорт в системы, которые поддерживаются адаптерами логстеша.

В данной конфигурации настроен экспорт в эластик.

# Реализация
Решение предоставляется в виде docker-compose файла для запуска в любой среде поддерживающей контейнеры, а так же файлов конфигурации для него.

Конфигурация настройки пайплайна обработки находится в файле [logstash-tj.config](./logstash/pipeline/logstash-tj.config)
Паттерны выражений в файле [patterns](./logstash/pipeline/patterns) 

# Запуск

Выполнить команду: docker-compose up -d

Положить логи в ./logs