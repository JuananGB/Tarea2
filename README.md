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
