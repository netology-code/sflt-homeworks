# Домашнее задание к занятию 2 «Кластеризация и балансировка нагрузки»
**Косарев Д.О.**

## Задание 1: Round-robin на 4 уровне

### Конфигурационный файл HAProxy:
[roundrobin-l4.cfg](haproxy-configs/roundrobin-l4.cfg)

### Доказательство работы:
![Скриншот работы HAProxy](images/Screenshot%20from%202025-10-07%2023-19-21.png)

## Задание 2: Weighted Round Robin на 7 уровне

### Конфигурационный файл HAProxy:
[weighted-l7.cfg](haproxy-configs/weighted-l7.cfg)

### Доказательства работы:
![Скриншот 1 - Запросы с доменом example.local](images/Screenshot%20from%202025-10-07%2023-27-26.png)

![Скриншот 2 - Распределение по весам](images/Screenshot%20from%202025-10-07%2023-34-13.png)

![Скриншот 3 - Ошибка 404 без домена](images/Screenshot%20from%202025-10-07%2023-42-05.png)
