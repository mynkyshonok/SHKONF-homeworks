## Описание Ansible проекта:

Проект имеет: 
 - файл плейбука site.yml
 - Inventory файл с двумя группами хостов Clickhouse и Vector
 - папка с группированными переменными по группам хостов Clickhouse и Vector
 - папка template с шаблонами jinja2

Плейбук состоит из двух плеев Clickhouse, Vector:
 - Clickhouse:
   Для группы хостов Clickhouse производит скачивание Clickhouse версии указанной в переменной "clickhouse_version", установку Clickhouse и создание БД.
 - Vector:
   Для группы хостов Vector производит скачивание Vector версии указанной в переменной "vector_version", установку Vector (установка бинарника, создание конфига из template j2, создание unit файла systemd из template j2, запуск службы)


ansible-lint site.yml:

<img width="1025" height="211" alt="image" src="https://github.com/user-attachments/assets/fb21488c-c521-4e88-b90b-4c4023d7a8a1" />

плейбук применён:

<img width="832" height="84" alt="image" src="https://github.com/user-attachments/assets/76af3f4a-9377-4da6-b655-67064613792f" />
