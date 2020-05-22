---
title: Estructura básica de un componente Vue
permalink: estructura_basica_de_un_componente_vue.html
folder: vuejs
---
{% include note.html content='referencias: https://www.freecodecamp.org/news/how-to-create-a-vue-js-app-using-single-file-components-without-the-cli-7e73e5b8244f/' %}

## HTML, JavaScript y CSS en un mismo archivo

  Los Single File Components son útiles para proyectos grandes donde la opción de definir componentes globales puede complicar la existencia a grupos de desarrolladores por las siguientes razones:

  - Se debe tener un nombre para cada componente.
  - Los string templates se vuelven complicados y no tienen resaltador de sintaxis en la definición de los templates.
  - No podemos modularizar el CSS.
  - No podemos utilizar transformaciones, es decir, no podemos trabajar con preprocesadores de html y/o js que nos ayuden en la productividad.
  
  Crearemos manualmente un proyecto desde cero para configurar el uso de SFC y luego lo haremos con ayuda de vue-cli.

  Si antes para un sitio web necesitábamos crear las carpetas /css /js /assets, ahora esas carpetas (no exactamente esas), serán creadas por webpack y las dependencias (como vue y otras librerías), serán manejadas por npm o yarn. Entonces para separar nuestro código de los que generará webpack, pondremos los archivos para desarrollar en otra carpeta, normalmente llamada /src y acá tendremos los componentes .vue, el index.html y el archivo js principal main.js o index.js.

  En la raíz del proyecto necesitaremos el archivo con las dependencias (package.json), el archivo de configuración para Webpack y el archivo de configuración para Babel (usaremos Babel para usar ES6), también podríamos agregar otros archivos para la configuración de otras herramientas como Typescript, pero de momento solo usaremos Babel.

  El directorio del proyecto quedaría de la siguiente forma:

![alt text][sfc_zero_0]

[sfc_zero_0]: /images/sfc_0.png "Initial project folder"  

Ahora nos falta agregar todas las dependencias para que webpack pueda transformar los códigos en /src. De hecho, el mismo Webpack y sus plugins (loaders) son también dependencias. Primero vamos a instalar todo lo necesario de Webpack:

```bash
$ yarn add -D webpack webpack-dev-server webpack-cli html-webpack-plugin
```

Además de webpack se agrega el servidor para desarrollo, el cli para ejecutar comandos y el plugin que incluirá el resultado en el html y lo copiará en una carpeta que creará llamada /dist.

Ahora seguiremos con Vue:

```bash
$ yarn add -D vue vue-loader vue-template-compiler vue-style-loader
```

Primero el framework en sí y luego las dependencias para usar SFC

Continuaremos con lo necesario para trabajar con Babel:

```bash
yarn add -D babel-loader @babel/core @babel/preset-env
```

Finalmente agregaremos el cargador de CSS que trabajará junto con vue-style-loader para agregar lo necesario al head del index.html

```bash
yarn add -D css-loader
```
Con las dependencias instaladas es momento de configurar Webpack y Babel:

```js
/*
  ./webpack.config.js
  Primero se requieren los plugins, los módulos normalmente no se requieren
  antes
*/
const HtmlWebpackPlugin = require('html-webpack-plugin');
const VueLoaderPlugin = require('vue-loader/lib/plugin');

module.exports = { // La configuración completa se exporta como un objeto
  entry: './src/main.js', // El archivo js principal
  module: { // Los módulos se configuran con una regex sobre las extensiones de los archivos
    rules: [
      { test: /\.js$/, use: 'babel-loader' },
      { test: /\.vue$/, use: 'vue-loader' },
      { test: /\.css$/, use: ['vue-style-loader', 'css-loader']},
    ]
  },
  plugins: [ // Finalmente se instancian los plugins
    new HtmlWebpackPlugin({
      template: './src/index.html',
    }),
    new VueLoaderPlugin(),
  ]
};
```
```js
module.exports = {
  presets: ['@babel/preset-env'],
}
```

Ahora con el proyecto configurado podemos escribir los archivos de la aplicación. Partiremos con App.vue, el componente de un solo archivo

```js
// src/App.vue
<template>
  <div id="app">
    {{ message }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'SFC desde cero',
    };
  },
};
</script>

<style>
#app {
  font-size: 18px;
  font-family: 'Roboto', sans-serif;
  color: blue;
}
</style>
```

Ahora el index.html 

```html
<html>

<head>
  <title>Vue SFC</title>
</head>

<body>
  <div id="app"></div>
</body>

</html>
```

Listo! Ahora para levantar el proyecto, es decir, hacer todas las transformaciones necesarias y desplegar el proyecto en el navegador debemos ejecutar el siguiente comando:

```bash
$ yarn run webpack-dev-server --mode development
```

O escribir este comando en el package.json para luego solo ejecutar ```$ yarn run serve ```

```js
// Por convención los la llave scripts va previo a las dependencias
...
"scripts": {
    "serve": "webpack-dev-server --mode development"
  },
...  
```
El proyecto en el navegador con la consola de inspección de Vue se verá de la siguiente forma:


![alt text][sfc_1]

[sfc_1]: /images/sfc_1.png "Hello SFC"  



## Montar componente en elemento HTML
## Conociendo el objeto data. Diferencias entre One/Two way binding.
## Formularios y directiva model