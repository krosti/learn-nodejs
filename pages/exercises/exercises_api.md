---
permalink: exercises_api.html
title: Globant NodeJS practice project 🙌
---

El objetivo es armar una API para poder mostrar los respositorios de un usuario y su información en la aplicación frontend especificada en [angularjs-practice](/angularjs-practice)

## Server side (API)

### Implementar los siguientes endpoints:
* obtener los repositorios de un usuario
* obtener la información de un repositorio del usuario
* obtener el listado de commits de un repositorio
* obtener la información de un commit especifico dentro de un repositorio
* obtener el listado de pull request de un repositorio
* obtener la información de una pull request especifica dentro de un repositorio
* obtener la información del autor de un commit cualquiera sobre el último _pull request_ realizado, dado un repositorio.

### Criterios de aceptación:
* todos los endpoints deben devolver un JSON y deben contener toda la informacion que devuelve github
* todos los endpoints deben tener tests donde se verifiquen los casos de éxito y de falla (considerar también los casos en que no se pueda establecer una conexión con la API de Github)
* Los test se deben ejecutar con grunt

### Tools
* NodeJs
* Restify
* Async o Q (promises)
* Grunt como task runner

No hay limitaciones en cuanto a la utilización de herramientas, librerias o plugins adicionales.
