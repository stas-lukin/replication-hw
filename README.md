# Домашнее задание к занятию «Репликация и масштабирование. Часть 1»

**Студент:** Лукин Станислав

## Задание 1. Различия режимов репликации

**Master-Slave:** Один главный сервер (master) принимает запись, один или несколько подчинённых (slave) только читают. При отказе master необходимо ручное переключение.

**Master-Master:** Оба сервера могут принимать запись. Требует разрешения конфликтов. Сложнее в настройке, но обеспечивает более высокую доступность записи.

## Задание 2. Конфигурация master-slave репликации

### Конфигурация master (файл master.cnf)

```ini
[mysqld]
server-id = 1
log-bin = mysql-bin
binlog-format = ROW
```

![Конфиг master](repl_master_conf.png)

### Конфигурация slave (файл slave.cnf)

```ini
[mysqld]
server-id = 2
read-only = 1
```

![Конфиг slave](repl_slave_conf.png)

### Статус master (SHOW MASTER STATUS)

![Master status](repl_master_status.png)

### Статус slave (SHOW REPLICA STATUS\G)

![Slave status](repl_slave_status.png)
