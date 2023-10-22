# Comenzamos con Docker Normal
Aquí explicaremos paso a paso de manera sencilla cómo crear un contenedor con docker.

Primero abriremos una nueva terminal, para separar GIT de docker

Para iniciar Docker debemos hacer

    sudo docker run -it (nombre de la imagen) bash

## Opciones
Existen varias opciones a elegir despues de poner  **docker  run**

**-i (interactive)** se utiliza para mantener abierta la entrada estandar en el terminal , es decir una vez ejecutas el comando que ya estes dentro del contenedor

**-t (TTY)** hace que el -i sea más práctico ya que nos da más información de la consola

**Ejemplo:**
    Tras crear la imagen de ubuntu bash si con -i hacemos ls, nos mostrará el resultado normal
        
    sbin
    srv
    sys
    tmp
    usr
    var

PERO, SI AÑADIMOS -T NOS DÁS MAS INFORMACIÓN, YA QUE NOS MUESTRA LO SIGUIENTE:
   
    root@31338c5f2df8:/# 


**-d (detach)** Esto nos sirve para correr el contenedor en **Segundo plano** y no entrar directamente en la terminal en este caso

todos estos comandos se puedn combinar tal que así
 **-dit**

# Comprobaciones

Cuandlo añadimos  **-d** cómo podemos comprobar si todo ha funcionado correctamente osando los siguientes comandos:

**Docker ps**
---

**Docker ps** a secas muestra los contenedor es en Actual funcionamiento

**Docker ps -a** muestra los contenedoses en funcionamiento además de los detenidos

**Docker ps -q** muestra una lista de solo los id de los contenedores

    Obviamente todo esto se puede combinar
        Docker ps -qa




Nombres DOCKER
---
Bien a continuacióin aprenderemos como ponerle un nombre a docker, ya que cómo lo estabamos creando antes se le asignaba uno aleatorio.

esto se hace con **--name** + el nombre que le queramos asignar

    docker run --name NombreDelContenedor -it ubuntu


    marcosfa@MacBook-Pro-de-Marcos Practica_examen % docker ps
    CONTAINER ID   IMAGE                  COMMAND                  CREATED          STATUS          PORTS                 NAMES
    7ea3010a62a4   ubuntu                 "/bin/bash"              10 seconds ago   Up 10 seconds                         contenedorConNombre


## IMPROTANTE

Pongamos por caso que hemos creado un contenedor erroneamente y queremos eliminarlo, estio lo podremos hacer con el comando

    docker rm nombre_contenedor

Si por el contrario hemos creado un congtenedor con **-d** y queremos acceder a el por su nombre, será tan secillo como ejecutal el siguiente comando

    docker exec -it nombreContenedor bash (si queremos abrir la terminal)


### Practicas:

Una de las prácticas que se nos puede pedir será hacer ping a cierta ip, o comprobar que ip tenemos, esto por defecto no viene instalado en ubuntu, por lo que deberemos hacer lo siguiente.


    apt update
    apt install iputils-ping
    apt install net-tools

Con los comandos **ping** o **ifconfig** podremos solucionar estos ejercicios.

## Más info

Para saber cuantos recursos está consumiendo **Docker** podemos efectuar el siguiente comando:

    docker system df




