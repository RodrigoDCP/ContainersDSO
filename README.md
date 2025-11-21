## 1. Mac
---
1. ¿Qué modelo de Mac?
~~~
Mac Pro 2019
~~~

2. ¿Cuánta memoria ram tiene?
~~~
96gb en ram a 2666Mhz en DDR4
~~~

3. ¿Qué procesador tiene?
~~~
Intel Xeon W de ocho núcleos a 3.5Ghz
~~~

4. ¿Cuántos núcleos tiene?
~~~
8 núcleos
~~~

5. ¿Cuántos hilos tiene el procesador?
~~~
16 hilos
~~~

6. ¿Qué tarjeta de vídeo tiene?
~~~
AMD Radeon Pro W5500X
~~~

### 1.1. Anexos
---

![](Anexos/image01.png)

![](image02.png)

![](image03.png)


## 2. Docker en MAC
---
Primero se realizo la preparación del entorno de trabajo, creando una carpeta donde tendremos los recursos que serán necesarios para el sistema de contenedores 

~~~bash
mkdir moodle-docker
~~~

Dentro de la carpeta, clonaremos el repositorio que el documenta nos recomienda para trabajar (contiene las utilidades necesarias para el sistema).

~~~bash
git clone https://github.com/bitnami/containers.git
~~~

Por ultimo, creación de la red:

~~~bash
docker network create moodle-network
~~~

### 2.1. Creación de contenedores
---
Una vez clonado el repositorio, nos dirigimos a las versiones disponibles para crear el moodle, para nuestro caso, encontramos disponible la versión ``5.1`` de ``debian-12``, con esto, construiremos la imagen que será nuestro punto de partida a la creación de los contenedores.

Para crear la imagen, se utilizo el siguiente comando a partir del ``DockerFile`` del repositorio:

~~~bash
docker build -t bitnami/moodle:5.1 .
~~~

![](image04.png)

Mismo procedimiento se realiza para la base de datos:

~~~bash
docker build -t bitnami/mariadb:5.1 .
~~~

![](image05.png)

Finalmente, utilizando docker compose, podremos levantar los contenedores con las 2 imágenes ya creadas:

~~~bash
docker compose up -d
~~~

![](image06.png)

### 2.2. Configuración básica
---

Primero se añadió un curso, esto desde las configuraciones de cursos:

![](image07.png)

Seguido de eso se agregaron los usuarios con los datos solicitados:

![](image08.png)

Finalmente en el curso se realizo la asignación de roles, cumpliendo con el ejemplo del documento:

![](image09.png)


## 3. Conclusiones
---
**Rodrigo David Cañas Pérez:**
Esta actividad me permitió comprender de manera práctica el funcionamiento de Docker Compose y su utilidad para orquestar múltiples contenedores. Aunque inicialmente el proceso de construcción de imágenes requirió paciencia, el resultado final demostró la eficiencia de esta herramienta para gestionar servicios acoplados, como Moodle y MariaDB. Aprendí a configurar roles y usuarios dentro de la plataforma, lo que reforzó mi entendimiento sobre la integración entre contenedores y aplicaciones web. Considero que ha sido un ejercicio muy valioso para afianzar conceptos clave de DevSecOps.

**Enrique Manzanilla Pacheco:**
Esta tarea me ayudó a entender mejor cómo funciona Docker Compose en un entorno real. Aunque al inicio me costó un poco entender la estructura de los archivos, al final pude ver cómo todo se conecta: la base de datos con Moodle, los usuarios, los cursos… Fue satisfactorio ver todo funcionando con solo un comando. Creo que esto es muy útil para automatizar despliegues sin complicarse tanto. Buen trabajo en equipo.

---

Repositorio: ``https://github.com/RodrigoDCP/ContainersDSO``