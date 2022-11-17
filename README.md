## Playbook

Playbook производит развертывание необходимых приложений на указанные сервера. 
Для простоты деплоя все хосты сделаны доступными через интернет. 

- ### Clickhouse

  - установка `clickhouse`
  - настройка удаленных подключений к приложению
  - создание базы данных и таблицы в ней


- ### Vector

  - установка `vector`
  - изменение конфига приложения для отправки логов на сервер `clickhouse-01`

- ### Lighthouse

  - установка `lighthouse`
  - настройка `nginx`

## Variables

Через group_vars можно задать следующие параметры:
- `clickhouse_version`, `vector_installer_url`, `lighthouse_distrib` - версии устанавливаемых приложений;
- `clickhouse_database_name` - имя базы данных для хранения логов;
- `clickhouse_create_table` - структуру таблицы для хранения логов;
- `vector_config` - содержимое конфигурационного файла для приложения `vector`;
- блок конфигурации `nginx` для работы с `lighthouse`;

## Tags

- `clickhouse` производит полную конфигурацию сервера `clickhouse-01`;
- `clickhouse_db` производит конфигурацию базы данных и таблицы;
- `vector` производит полную конфигурацию сервера `vector-01`;
- `vector_config` производит изменение в конфиге приложения `vector`;
- `lighthouse` производит установку `lighthouse`.
- `drop_clickhouse_database_logs` удаляет базу данных (по умолчанию не выполняется);
