# 1. Tutorial
# 1.1. Correr tutorial

~~~bash
docker run -d -p 7070:80 docker/getting-started
~~~

# 2. Moodle
## 2.1. Preparación del entorno

~~~bash
mkdir moodle-docker
cd moodle-docker
~~~

~~~bash
git clone https://github.com/bitnami/containers.git
~~~

~~~bash
docker network create moodle-network
~~~
## 2.2. Creación de contenedores

~~~bash
docker build -t bitnami/moodle:5.1 .
~~~

~~~bash
docker build -t bitnami/mariadb:5.1 .
~~~

~~~bash
docker compose up -d
~~~
