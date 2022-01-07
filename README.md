# 📚 Crear una API-REST simulada para desarrollos frontend

Es posible construir una API simulada que permita realizar desarrollos sin necesidad de esperar que esté construida.
De una manera fácil y sencilla, se puede disponer de un servicio backend que sustituya al servicio definitivo que pueda estar en construcción.

Este servicio permitirá realizar llamadas http para obtener y guardar información utilizando el formato JSON.

>**Disclaimer:** Se trata de un resumen de la publicación realizada en CampusMVP en el siguiente [enlace](https://www.youtube.com/watch?v=dei0Sm3P9vA) 🎥.

Para ello necesitaremos disponer de:

* [Json Server](https://github.com/typicode/json-server)
  * Se trata de módulo software que construye el servicio web que nos permitirá prototipar los desarrollos frontend ofreciendo una API totalmente funcional.

* [NodeJS](https://nodejs.org/es/)
  * Entorno de ejecución aplicaciones Javascript con el cual lanzaremos el servicio web. Utilizaremos su gestor de paquetes para descargar Json Sserver.

* [Hoppscotch](https://hoppscotch.io/es/)
  * Se trata de una herramienta open source para el desarrolloo de API's, que utilizaremos para probar nuestro servicio simulado.
  
## 📝 Instrucciones

1. Setup. Es necesario tener instalador el entorno NodeJS (v12 o superior).
2. Crear una carpeta donde realizar guardar nuestro proyecto.
3. En el directorio de trabajo, inicializaremos un nuevo proyecto para NodeJS haciendo uso del gestor de paquetes npm, donde se creará el fichero _package.json_:
    * `npm int -y` 
    
>El fichero package.json alamacenará la dependencia Json Server.

4. Instalación del módulo npm _**Json Server**_
     * `npm i json-server -D` 
>El modificador _-D_ indica que se instalará la dependencia en modo desarrollo.

5. Crear el fichero que hará las veces de base de datos.
Añadiremos un nuevo fichero al directorio de trabajo con extensión .json y un nombre cualquiera.
Deberá contener objetos javascript que representarán los endpoints de la API, así como la información almacenada. En el siguiente ejemplo dichos endspoints serían _autores_, _posts_, y _comentarios_:
``` js
{
  "autores": [
    {
      "id": 1,
      "nombre": "Marcos Rodrigo"
    },
    {
      "id": 2,
      "nombre": "Isaac Rodrigo"
    }
  ],
  "posts": [
    {
      "id": 1,
      "titulo": "Cómo crear una API simulada para pruebas",
      "autor": 1
    },
    {
      "id": 2,
      "titulo": "Cómo usar una API simulada en frontend",
      "autor": 2
    }
  ],
  "comentarios": [
    {
      "id": 1,
      "mensaje": "Muy interesante!",
      "postId": 1
    },
    {
  ]
}
```

6. Lanzar el servicio web.
Para ello, en el fichero _package.json_ añadiremos una nueva tarea para que Node inicie el servidor y el servicio. El la sección _scripts_ del fichero añadiremos ``"servicio": "json-server --port 8081 --watch api.json"`` donde estamos indicando que se ejecute en un puerto concreto y asociado al fichero json que hace las veces de base de datos.
El fichero package.json tendrá el siguiente aspecto:
``` js
{
  "name": "api-rest-dev",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "servicio": "json-server --port 8081 --watch api.json"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "json-server": "^0.17.0"
  }
}
``` 
Finalmente el servicio lo lanzaremos ejecutando: ``npm run servicio`` 