## Paso 1. Descargar la imagen "alpine" sin arrancarla y comprobar si está en el equipo.

-Descargar la imagen: 

```bash
    docker pull alpine
```

-Comprobar si se descargó correctamente: 

```bash
    docker images
```

## Paso 2. Crea un contenedor sin ponerle nombre.¿Está arrancado? Obtén el nombre.

-Crear un contenedor:

```bash
    docker create alpine
```
-Ver el estado de los contenedores:

```bash
    docker ps -a
```

## Paso 3. Crear un contenedor con el nombre "dam_alp1",¿Cómo puedes acceder a el?.

-Crear el contenedor, esta vez añadiendole un nombre:

```bash
    docker run --name dam_alp1 -d alpine tail -f /dev/null

```
* El comando tail -f /dev/null (mantiene el contenedor en ejecución)

-Como acceder al él:

```bash
    docker exec -it dam_alp1 sh
```

## Paso 4. Comprobar que ip tiene y si puedes hacer un ping a google

-Comprobar ip:

```bash
    docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' dam_alp1
```

-Hacer un ping a google:

```bash
    ping google.com
```
## Paso 5. Crear un contenedor con el nombre 'dam_alp2'. ¿Puedes hacer ping entre los contenedores?

-Crear contenedor dam_alp2:

```bash
    docker run --name dam_alp2 -d alpine
```
-Hacer un ping usando el contenedor dam_alp2::

```bash
    docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' dam_alp2
```
-Acceder al contenedor dam_alp1:

```bash
   docker exec -it dam_alp1 sh
```
-Dentro del contenedor dam_alp1 escribiremos este comando:

```bash
    ping [IP_DE_dam_alp2]
```
* Donde pone IP_DE_dam_alp2, escribimos la ip de dam_alp2

## Paso 6. Sal del terminal. ¿Qué ocurrió con el contenedor?

-Salir del terminal dentro del contenedor:

```bash
    exit
```
* Si dentro del contenedor estás imprimiendo la ip de dam_alp2, primero tienes que parar esse proceso, para poder salir del contenedor.

## Paso 7. ¿Cuánta memoria en el disco duro ocupaste?

-Memoria ocupada: 

```bash
    docker system df
```

## Paso 8. ¿Cuánta RAM ocupan los contenedores? ¿Hay algún comando Docker para saber esto?

```bash
    docker stats
```

