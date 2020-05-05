---
title: Instalar Vue.js
permalink: instalar_vuejs.html
folder: vuejs
---

## Requisitos
A pesar de que es posible desarrollar aplicaciones con Vue sin usar Node.js, si es necesario para usar la interface de líne de comandos Vue-cli y el gestor de dependencias NPM. Con ellos podremos prefabricar aplicaciones más rápido que hacerlo a mano. También podemos mejorar la experiencia de desarrollo usando las últimas versiones de ECMAScript.

### Windows

Descargar e Instalar Node directamente desde https://www.nodejs.org. Asegurar que la opción Add to PATH esté seleccionada (esto agrega un link a los ejecutables para poder usar el comando `node` en la terminal).|

Para asegurar la correcta instalación ejecutar los siguientes comandos:

`node -v`

`npm -v`

Al día de hoy Node esté en su versión 12.16 como la última estable y 6.14 para npm

### Mac
En Mac podemos usar Node Version Manager o NVM, el cual nos permite controlar diferentes versiones del interprete Node en el mismo equipo.


Ejecutar el siguiente comando con Homebrew. Si no lo tiene puede visitar http://brew.sh para las instrucciones de instalación

`brew install nvm`

Crear un directorio para los archivos de nvm

`mkdir ~/.nvm`

Esto instala la última versión estable con soporte (lts)

`nvm install --lts`

Con el siguiente comando aseguramos que el sistema esté usando node por nvm y no la instalación local

`nvm use node`

Para hacer permanente la configuración de NVM editaremos el archivo de perfil de usuario 

`nano ~./bash_profile`

Agregamos las siguientes linas, guardamos y salimos.
`export NVM_DIR="$HOME/.nvm"`

`. "$(brew --prefix nvm)/nvm.sh"`


### Ubuntu/Linux

Descargar y ejecutar nvm 

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash`

Reiniciar la terminal y luego agregar la última versión estable

`nvm install --lts`

## Vue devtools

Con Node en nuestro entorno de desarrollo ahora instalaremos una extensión para el navegador. Ingresar a la tienda de Extensiones de Chrome y descarga Vue.js devtools (https://goo.gl/Sc3YU1).

Con esto ahora tendremos acceso a un panel Vue dentro de la consola de inspección de crome. Veamos un ejemplo.
```html
<div id='dev-tools'></div>
<script>
Vue.config.devtools = true
new Vue({
  el: '#dev-tools',
  data: {
    name: 'Vue.js Devtools',
    browser: 'Google Chrome'
    },
  template: `
    <div>
      <h1>I'm using {{ name }} with {{ browser }}</h1>
    </div> `
  })
</script>
``` 
<div id='dev-tools'></div>
<script>
Vue.config.devtools = true
new Vue({
  el: '#dev-tools',
  data: {
    name: 'Vue.js Devtools',
    browser: 'Google Chrome'
  },
  template: `
  {% raw %}
  <div>
    <h1>I'm using {{ name }} with {{ browser }}</h1>
  </div>
  {% endraw %}
  `
})
</script>

Con lo anterior deberíamos ver algo como esto:

![alt text][logo]

[logo]: /images/dev-tools.png "Vue dev tools"