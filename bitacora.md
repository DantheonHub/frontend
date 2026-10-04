# Bitácora de clases — Frontend

Una línea por clase real, en el orden en que se dictaron. El detalle técnico de cada tema vive en `conceptos.md`.

* **Clase 1 — Presentación de la cursada e introducción a HTML**
  > **Contenido:** presentación del programa, objetivos y herramientas de la materia (Angular ≥17, VS Code, Git). Primera parte de la teoría de HTML: qué es HTML, metadatos, estructura en árbol, estructura básica de un documento, etiquetas, etiquetas semánticas vs. no semánticas, SEO y atributos.

## Clase 2 — Introducción a JavaScript

- **Contenido:**
  - origen de JavaScript y relación con ECMAScript;
  - motores y entornos de ejecución;
  - tipado dinámico y coerción;
  - scripts y algoritmos;
  - `var`, `let` y `const`;
  - scope de función y de bloque;
  - tipos primitivos, `null` y `undefined`;
  - objetos y arrays;
  - funciones tradicionales, funciones flecha y callbacks;
  - parámetros y argumentos;
  - asignación de primitivos y referencias compartidas entre objetos;
  - introducción a la gestión automática de memoria.

- **Práctica:** ejecución con Node.js, declaraciones y reasignaciones, scope, acceso y modificación de objetos y comparación entre asignaciones de primitivos y objetos.

- **Estado:** fundamentos de JavaScript iniciados; eventos y algunos comportamientos de `const` quedaron abiertos.

## Clase 3 — JavaScript: JSON, funciones y asincronía

- **Contenido:**
  - template literals e interpolación;
  - serialización con `JSON.stringify()` y recuperación con `JSON.parse()`;
  - diferencia entre objetos literales y JSON;
  - funciones, parámetros, argumentos y retornos;
  - sintaxis abreviada de arrow functions;
  - callbacks y funciones de orden superior;
  - introducción al hoisting de declaraciones de funciones;
  - asincronía y temporizadores con `setTimeout()`;
  - acceso y modificación de variables de ámbitos externos.

- **Práctica:** manipulación de objetos y JSON, funciones tradicionales y flecha, callbacks y seguimiento del orden de ejecución con temporizadores.

- **Estado:** funciones y callbacks consolidados a nivel introductorio; asincronía iniciada. Quedan pendientes eventos, promesas y una explicación más profunda del modelo de ejecución.


## Clase 4 — DOM, eventos, errores y arrays

- **Contenido:**
  - eventos y asociación de callbacks;
  - estructuras de control y operador ternario;
  - introducción al DOM;
  - manejo de excepciones con `try`, `catch` y `finally`;
  - arrays, índices, longitud y referencias;
  - métodos `filter`, `find`, `findIndex`, `some`, `every`;
  - métodos de modificación `push`, `pop`, `shift`, `unshift`, `fill` y `splice`;
  - copia parcial con `slice`;
  - recorrido con `forEach`;
  - concatenación y ordenamiento con `sort`.

- **Práctica:** creación y comparación de arrays, callbacks sobre colecciones, búsqueda y filtrado, inserción/eliminación de elementos y ordenamiento numérico.

- **Estado:** arrays desarrollados con bastante profundidad; DOM, eventos y manejo de errores quedaron introducidos para retomarse en la práctica.

## Clase 5 — DOM, eventos y módulos JavaScript

- **Contenido:**
  - vinculación de HTML con archivos CSS y JavaScript;
  - selección con `getElementById`;
  - modificación con `innerText` e `innerHTML`;
  - eventos `click`, `keydown` y `change`;
  - asociación desde HTML y mediante `addEventListener`;
  - lectura de valores de formularios;
  - modificación dinámica de estilos;
  - generación de contenido HTML desde arrays;
  - `setTimeout` para escalonar ejecuciones;
  - introducción a módulos con `export`, `import` y `type="module"`;
  - selección múltiple con `querySelectorAll` y recorrido de `NodeList`.

- **Práctica:** interacción entre controles HTML y JavaScript, modificación del DOM, construcción de listas y organización del código en módulos.

- **Estado:** práctica de DOM y eventos desarrollada; módulos introducidos. El ejercicio integrador final de módulos + eventos quedó pendiente de resolución.

## Clase 6 — Fundamentos de CSS

- **Contenido:**
  - estructura de reglas CSS;
  - CSS externo, interno e inline;
  - selectores universal, de tipo, clase, ID, descendientes y agrupados;
  - cascada y especificidad;
  - pseudo-clases y pseudo-elementos;
  - representación de colores;
  - bordes y `border-radius`;
  - unidades absolutas y relativas (`px`, `em`, `rem`, `%`);
  - fondos;
  - `margin`, `padding` y `overflow`;
  - box model y `box-sizing`;
  - introducción conceptual a Flexbox, Grid y `gap`.

- **Práctica:** aplicación y combinación de selectores, resolución de conflictos por especificidad, estilos de borde/fondo, medidas y comparación entre `content-box` y `border-box`.

- **Estado:** fundamentos de CSS iniciados y box model desarrollado; Flexbox y Grid quedaron introducidos para profundizar más adelante.


