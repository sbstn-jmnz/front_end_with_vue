---
title: Introducción a componentes web y Vue.js
permalink: introduccion_a_componentes_web_y_vuejs.html
folder: vuejs
---

## Qué es un componente web. Cuáles son sus características y por qué usarlos

Un componente web es una solución para la Interfáz de Usuarios que permite crear elementos independientes del documento principal con lógica y estilos propios. 

Son un conjunto de tecnologías usadas para la creación de elementos, personalizados y reutilizables en las aplicaciones web. Tienen su funcionalidad encapsulada del resto del código de la aplicación.

Esto se implementa agregando etiquetas al documento, con su comportamiento y lógica propios, sin correr el riesgo de que el código estropee otras partes de la interfaz. Ejemplos de estas etiquetas son <template> y <slot>, las cuales no son mostradas por en navegador en el flujo normal de carga del DOM. Estas etiquetas esperan ser ejecutadas por sus propios scripts. 

En general para crear estos componentes se requieren tres partes:

- Elementos personalizados (custom elements): Una interfáz js que define al elemento y su comportamiento. Una función o una clase con ES6. Puede ser creada o extender sobre elementos existentes nativos de HTML.
- DOM interno (shadow DOM):  Una interfaz que encapsula un DOM interno y propio del componente, el cual se dibuja separadamente en el DOM. De esta forma se puede mantener y programar por separado su estilo y funcionalidad
-  Planillas html (HTML templates): Son etiquetas html que no se muestran junto con la página o documento HTML (<template> o <slot>)

Con esto se busca crear interfaces altamente dinámicas sin complicar el código, aumentar la productividad y mantenibilidad de las aplicaciones web.


Referencias: [MDN Web Components](https://developer.mozilla.org/en-US/docs/Web/Web_Components "MDN Web Components")
[wikipedia Web Components](https://en.wikipedia.org/wiki/Web_Components)


## Qué es reactividad

La reactividad puede ser entendida como la programación que trabaja con flujos de datos asíncronos (cambios no sincronizados en los datos de entrada o salida). Muchas cosas pueden ser un flujo de datos (el movimiento del mouse, los feeds de Twitter, una variable, etc). Ahora podemos escuchar esos flujos (streams) y reaccionar según lo que va llegando. 

Esto de trabajar con flujos de datos permite a la programación funcional pasar los datos por muchos flujos, combinarlos y filtrarlos. Podríamos, de muchos eventos, suscribirnos a algunos específicos e ignorar otros.

La reactividad agrega un eje del tiempo a la lógica de la programación web más tradicional. Las aplicaciones web anteriormente de centraban más en cambios discretos, pero ahora cualquier evento pude ser capturado, procesado y afectar los componentes de la interfaz. 

La programación reactiva combina varios patrones de diseño y hay implementaciones casi todos los lenguajes de programación más populares.  

## Ejemplos de librerías o frameworks que lo utilizan (React, Angular, Vue)

En el frontend hay varios frameworks que pueden incorporar reactividad para trabajar con stream de datos. Tanto React, Angular, Vue y otros pueden adoptar estas técnicas.

## Similitudes y diferencias

React es más parecido a Vue ya que ambas se centran en crear interfaces para aplicaciones web. React para generar las plantillas usa JSX, el que permite un estilo más declarativo, mientras que Vue usa directamente plantillas en HTML. Ambas tienen compatibilidad con librerías adicionales para manejar el estado de la aplicación (Redux & Vuex).   

Por su parte, Angular, es un framework completísimo, el cual es mucho más grande y fomenta una arquitectura más estricta para aplicaciones web complejas. Lo mismo en el caso de Ember. De todos estos frameworks, Vue presenta una alternativa progresiva. Es posible incorporar Vue en pequeñas cantidades a proyectos existentes o hacer aplicaciones SPA[^1] o PWA[^2]. Eso tiene como costo que muchas de las decisiones de arquitectura (cómo organizar el código) son dejadas en manos del desarrollador o un framework de Vue como Quasar.

Todos estos frameworks intentan apoyar el desarrollo de interfaces altamente dinámicas en las que los patrones clásicos de recorrer el DOM y actualizarlo según los eventos emitidos( como JQuery) presentan complicaciones en performance (recorrer el DOM cuesta trabajo sorbe todo cuando el DOM es complejo) y además complejo de mantener y modificar.  

## ¿Qué es Vue JS? ¿Por qué usarlo? ¿Quienes lo utilizan?
Vue.js es un framework javascript de código abierto para construir interfaces de usuario. Permite construir completas aplicaciones web (SPA, PWA), widgets y extensiones.

Cómo lo indica en su [sitio web](https://vuejs.org/v2/guide/), Vue es un entorno de trabajo (framework) para construir interfaces de usuario. El corazón de Vue es un sistema que permite a los desarrolladores declarar como representar información o datos en el DOM usando etiquetas y Javascript simples como los siguientes ejemplos:

```html
{% raw %}
<div id="app">
  {{ message  }}
</div>
{% endraw %}
```

```javascript
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hola Vue!'
  }
})
```
Lo anterior, al ejecutar resulta lo siguiente:

<div id="app">
{% raw %}
  {{ message  }}
{% endraw %}
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hola Vue!'
  }
})
</script>
<br>

Vue fue creado por Evan You en 2014 mientras trabajaba en Google y está pensado para ser adoptado de forma incremental, por lo que puede ser rápidamente añadido a proyectos existentes para agilizar y refactorizar interfaces, pero también pude ser usado para crear productos completos en base a Vue. 

A diferencia de JQuery, Vue es un framework que permite obtener aplicaciones de alto rendimiento, con Angular comparten varias funcionalidades, pero con diferente implementación  y al igual que React usa un Dom Virtual con un enfoque orientado a componentes. Pero su sistema de plantillas es más simple y no require de JSX, que hace más fácil la integración de equipos dedicados (diseñadores y developers).

Vue tiene una curva de aprendizaje más fácil que otros frameworks, tiene buen rendimiento y una excelente documentación. Estas ventajas lo hacen un buen candidato para muchos proyectos. Tanto es así que grandes corporaciones como Facebook, Netflix, Adobe, Xiaomi y Alibaba tienen soluciones usando este framework.

## Alternativas a Vue JS

Sin orden específico es posible mencionar

  * Angular
  * AngularJs
  * React
  * Ember
  * Polimer
  * Aurelia
  * Preact
 
 En el curso nos enfocaremos en el desarrollo frontend en general, usando a Vue como una herramienta de alta productividad y fácil adopción. Si en el desempeño profesional tiene que trabajar con otro framework, de igual forma encontrará patrones y abstracciones similares para solucionar las problemáticas propias del desarrollo frontend  como lo son el manejo del estado, routing, reactividad, componentes, pruebas, server side rendering e integración con apis por mencionar algunos.

## El patrón de diseño MVVM

El patrón Modelo-Vista-Vista/Modelo, es un patrón estructural, donde la vista (view o template) es estática y sin lógica, compuesta por un lenguaje de marcado como HTML y estilos CSS (caso de las aplicaciones web) la cual despliega datos o información que proviene de los modelos. Al medio existe la capa Vista-Modelo, encargada de implementar la lógica de presentación. El patrón fue pensado para simplificar la programación guiada por eventos en las interfaces de usuario.

La principal diferencia con otros patrones estructurales como MVC o MVP es que el ViewModel implementa un enlace (binder) con las propiedades de la vista para desplegar el estado de la aplicación. 

Los modelos pueden ser desde simples arrays, el Local Storage del navegador o una fuente de bases de datos reactiva. También definen la estructura de los datos y sus reglas de validación. 

[^1]: Single Page Application.
[^2]: Progressive Web Application.