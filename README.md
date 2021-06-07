# Aplicación web en vue 3 y bootstrap 4.6

Aplicación creada en vue 3 y framework Bootstrap 4, esta aplicación permite mostrar anuncios que vienen de un api y muestra, imagen, titulo, precio, descripción del producto publicado. Podrás buscar y filtrar por tipo de publicación, por rango de precios de manera asíncrona.

En la parte superior encontrara un botón (contáctanos) que abrirá un modal, con el formulario de enviar un correo electrónico, esta función de enviar un correo electrónico no funciona porque lo que se requiere es que el mensaje se guarde en una base de datos, por lo tanto por medio de la API  http://localhost/api/emails se crea en la base de datos ese mensaje.

Problemas al usar VUE 3 y BootsTrap 4 es que vue no funciona bien con jQuery por lo tanto el modal de bootstrap no funciona, en la documentacion de vue explican como usar Modal Componet.

*** Complicaciones con bootstrap 4.6
por todas las complicaciones que tuve tratando de usar Vue 3 y bootstrap 4, no recomiendo mucho integrar la version 4 de bootstrap ya que este depende mayormente de JQuery y me genero muchos conflictos. 

* Puedes descargar la aplicación construida específicamente para este proyecto ya que ahí están generadas las APIs para que funcione.

*** Documentacion de aplicacion Backend de APIs.
[laravel-8-api-cambalache](https://github.com/rogeriocz/laravel-8-api-cambalache)



## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
