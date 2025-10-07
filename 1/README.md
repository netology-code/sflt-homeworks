
# Домашнее задание к занятию 2 «Кластеризация и балансировка нагрузки»
**Косарев Д.О.**

## Задание 1:

### Конфигурационный файл HAProxy:

\`\`\`cfg
global
    daemon
    maxconn 256

defaults
    mode tcp
    timeout connect 5000ms
    timeout client 50000ms
    timeout server 50000ms

frontend http_front
    bind *:8080
    default_backend http_back

backend http_back
    balance roundrobin
    server web1 127.0.0.1:8001 check
    server web2 127.0.0.1:8002 check
\`\`\`

![Скриншот работы HAProxy](images/Screenshot%20from%202025-10-07%2023-19-21.png)

## Задание 2

### Конфигурационный файл HAProxy:

\`\`\`cfg
global
    daemon
    maxconn 256

defaults
    mode http
    timeout connect 5000ms
    timeout client 50000ms
    timeout server 50000ms
    option httplog

frontend http_front
    bind *:8080
    acl is_example_local hdr(host) -i example.local
    use_backend http_back if is_example_local
    default_backend no_match

backend http_back
    balance roundrobin
    server web1 127.0.0.1:8001 weight 2 check
    server web2 127.0.0.1:8002 weight 3 check  
    server web3 127.0.0.1:8003 weight 4 check

backend no_match
    errorfile 503 /etc/haproxy/errors/404.http
\`\`\`

### Скриншоты работы:

![Скриншот 1](images/Screenshot%20from%202025-10-07%2023-27-26.png)

![Скриншот 2](images/Screenshot%20from%202025-10-07%2023-34-13.png)

![Скриншот 3](images/Screenshot%20from%202025-10-07%2023-42-05.png)
