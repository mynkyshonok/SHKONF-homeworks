## Описание Ansible проекта:

[Ссылка на коммит](https://github.com/mynkyshonok/SHKONF-homeworks/commit/6807e9adcba5243f83dcfaf7a70f4ec95aac248a)

Проект имеет: 
 - файл плейбука site.yml
 - Inventory файл с тремя группами хостов clickhouse, vector, lighthouse
 - папка group_vars с переменными
 - папка template с шаблонами jinja2

Переменные:
Для clickhouse:
   - "clickhouse_version" - версия clickhouse
Для vector:
   - "vector_version" - версия vector
Для lighthouse:
   - "lighthouse_archive_url" - url архива
   - "lighthouse_root_dir" - путь до папки со статикой

Плейбук состоит из трёх плеев Install Clickhouse, Установка Vector, Установка LightHouse:
 - Install Clickhouse:
   Для группы хостов Clickhouse:
     - Скачивание Clickhouse версии указанной в переменной "clickhouse_version"
     - Установка Clickhouse
     - создание БД.
   
   Хэндлер: Перезапуск службы clickhouse

 - Установка Vector:
   Для группы хостов Vector:
     - Скачивание Vector версии указанной в переменной "vector_version"
     - Создание директории для распаковки Vector
     - Распаковка Vector
     - Копирование бинарника
     - Создание папки с конфигом
     - Создание директории для данных Vector
     - Копирование конфига Vector из Jinja2 шаблона
     - Копирование systemd unit-файл для Vector
     - Активация и запуск сервиса Vector
   
   Хэндлер: Перезапуск службы Vector

 - Установка LightHouse:
   Для группы хостов LightHouse:
     - Обновление кэша пакетов APT
     - Установка Nginx и утилиты Unzip
     - Скачивание и распаковка архива со статикой lighthouse
     - Создание конфига Nginx из шаблона Jinja2
     - Включение конфига
     - Отключение дефолтного конфига Nginx
     - Активация и запуск службы Nginx
   
   Хэндлер: Перезапуск службы Nginx
