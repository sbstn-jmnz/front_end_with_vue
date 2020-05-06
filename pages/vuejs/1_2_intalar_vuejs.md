---
title: Instalar Vue.js
permalink: instalar_vuejs.html
folder: vuejs
---

## Formas de instalar Vue en una apicación web

Como framework progresivo, Vue.js nos permite incorporar sus funcionalidades de varias formas. Directamente desde un CDN para prototípos o pequeñas funcionalidades en sitios o aplicaciones legacy, o crear nuestra propia arquitectura con herramientas de desarrollo basadas en Node.js como NPM o YARN para configurar los proyectos usando Babel, TypeScript, Webpack, etc (los que estudiaremos en esta sección). Y finalmente, podemos instalar Vue.js y generar sencillamente proyectos y arquitecturas completas con la principal herramienta de desarrollo: la Interfáz de Linea de Comandos Vue CLI  

### CDN
En este mismo documento estamos integrando Vue mediante CDN. ¿Cómo crees que hago esto?.

<div id='buhoo'>
  <h1> 
  {% raw %} 
    {{ message }}  
  {% endraw %}
  </h1>
  <br>
    <input v-model='message' class='form-control' placeholder='Dí algo...'>
  <br>
</div>

<script>
new Vue({
  el: '#buhoo',
  data: {
    message: ''
  }
})
</script>



Solo basta con agregar esta etiqueta en el documento HTML para obtener una versión para desarrollo del framework (para l@s curioso, ¿Cuantas líneas de código tiene? Mirando las primeras líneas. ¿Qué tipos de dato Vue considera 'primitivos'?. ¿Tiene muchas más o menos líneas que JQuery?) 

```html
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

```

Si queremos una versión optimizada para produción (comprimida y minificada) debemos utilizar el siguiente tag:

```html
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

### NPM / Yarn

De esta forma podemos descargar Vue como dependencia a los proyectos y tener total control y responsabilidad sobre el proceso de desarrollo (recomendado para proyectos grandes y corporativos). Esto significa que podemos integrar Webpack o Browserify para transformar código fácil de estructurar y programar para los desarrolladores a código que es eficiente para el navegador.

Solo hace falta el siguiente comando: 
```bash
# instala la última estable
  $ npm install vue
```

Podemos lograr lo mismo con Yarn
```bash 
$ yarn add vue

```

### Vue CLI

Esta herramienta de línea de comandos nos permitirá generar estructuras de proyectos Vue completos con muchas opciones frecuentemente usadas. Actualmente soporta configuraciones para trabajar con Webpack, Browserfy y PWA.

Todo esto lo podríamos hacer manual, pero podemos ahorrar mucho tiempo usando Vue CLI para generar las configuraciones necesarias.

Para instalar Vue CLI ejecutar el siguiente comando

`npm install -g @vue/cli`

## Setup de una aplicación con Vue CLI y sus características agregadas

Veamos ahora algunas de las opciones que nos entrega Vue CLI
### Babel
### PWA
### Router
### Vuex
### Preprocesadores CSS
### Linters
### Testing
## Herramientas de desarrollo 
### Webpack
### Vue.js Devtools

Ahora instalaremos una extensión para el navegador. Ingresar a la tienda de Extensiones de Chrome y descarga Vue.js Devtools (https://goo.gl/Sc3YU1).

Con esto ahora tendremos acceso a un panel Vue dentro de la consola de inspección de Chrome. Veamos un ejemplo:

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

Con lo anterior deberíamos ver la pestaña `Vue` la terminal Javascript del navegador y ver la definición del objeto data como en la siguiente imagen:

![alt text][logo]

[logo]: /images/dev-tools.png "Vue dev tools"

## Extensiones para VS Code

Estas dos extensiones permiten mejorar el entorno de desarrollo para proyectos con Vue.js:

### Vetur 

Click en el ícono Extensions y busca por Vetur, selecciona instalar y listo! Con esto quedará automático para todos lo proyectos con Vue.js  
Para probar Vuetur puedes tipear `<vue` y luego tabular para obtener un sencillo y útil snippet como en ls siguientes
imágenes

![alt text][vue_tur_one]

[vue_tur_one]: /images/vuetur_one.png "Vue dev tools"

![alt text][vue_tur_two]

[vue_tur_two]: /images/vuetur_two.png "Vue dev tools"

### Vue 2 Snippets

Similar a lo hecho con Vetur, buscamos en las extensiones por Vue 2 snippetes e installar. Esto nos permitirá tener snippets de objetos Vue como en los siguientes pantallazos


![alt text][vue_snippets_one]

[vue_snippets_one]: /images/vue2snippets_one.png "Vue dev tools"

![alt text][vue_snippets_two]

[vue_snippets_two]: /images/vue2snippets_two.png "Vue dev tools"


