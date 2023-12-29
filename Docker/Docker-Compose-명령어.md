## docker compose 명렁(https://docs.docker.com/engine/reference/commandline/compose_exec/)
- docker-compose 는 지원 종료 예정 (https://docs.docker.com/compose/migrate/)

### docker-compose.yml
```
version: "3.8"

services:
  [service name]:
    image: redhat/ubi8:8.9
    container_name: [container name]
    volumes:
    - ./:/home/redhat-8.9
    network_mode: "host"
    stdin_open: true
    tty: true
  [service name]:
    image: redhat/ubi8:8.9
    container_name: [container name]
    volumes:
    - ./:/home/redhat-8.9
    network_mode: "host"
    stdin_open: true
    tty: true
```