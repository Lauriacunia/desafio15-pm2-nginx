### 🌈 Consigna 🌈

#### 🔥 1 - Pasar un parámetro por consola que permita ejecutar al servidor en modo fork o cluster (crear un if en el codigo). De no pasarlo, el servidor iniciará en modo fork.

- ver en punto 3)

- Linea 10 del archivo server.js

#### 🔥 2 - Agregar en la vista info, el número de procesadores presentes en el servidor (con os).

```
import os from "os"; // es propia de node para obtener informacion del sistema
const nroCPUs = os.cpus().length;
```

#### 🔥 3 - Ejecutar el servidor (modos FORK y CLUSTER) con nodemon verificando el número de procesos tomados por node. (en el package json)

```
 "cluster": "MODO='cluster' nodemon server.js",
 "fork": "MODO='fork' nodemon server.js"
```

#### 🔥 4 - Ejecutar el servidor (con los parámetros adecuados) utilizando Forever, verificando su correcta operación. Listar los procesos por Forever y por sistema operativo 💩

#### 🔥 5 - Ejecutar el servidor (con los parámetros adecuados: modo FORK) utilizando PM2 en sus modos modo fork y cluster. Listar los procesos por PM2 y por sistema operativo.

- modo fork. No envio PORT asi que toma el default

```
> pm2 start server.js  --name="serverFork" --watch
```

- modo cluster. Con 4 cpus de las disponibles

```
> pm2 start server.js --name="serverCluster" --watch -i 4

```

> pm2 list

#### 🔥 6 - Tanto en Forever como en PM2 permitir el modo escucha, para que la actualización del código del servidor se vea reflejado inmediatamente en todos los procesos.

> --watch

#### 🔥 7 - Hacer pruebas de finalización de procesos fork y cluster en los casos que corresponda.

> pm2 stop all
> pm2 delete all

### Configurar NGINX

#### 🔥 8 - Redirigir todas las consultas a /api/randoms a un cluster de servidores escuchando en el puerto 8081. El cluster será creado desde node utilizando el módulo nativo cluster. El resto de las consultas, redirigirlas a un servidor individual escuchando en el puerto 8080.

#### 🔥 9 - Luego, modificar la configuración para que todas las consultas a /api/randoms sean redirigidas a un cluster de servidores gestionado desde nginx, repartiéndolas equitativamente entre 4 instancias escuchando en los puertos 8082, 8083, 8084 y 8085 respectivamente.

- Tomo prestado el archivo de configuración de Leandro Wagner. Ver en carpeta

### Incluir en la entrega:

- Archivo de configuración de NGINX
- Documentación con los comandos a ejecutar en la terminal.
