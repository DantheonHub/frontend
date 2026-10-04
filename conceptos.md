# Frontend — Biblioteca de conceptos

Esta biblioteca organiza el conocimiento de la materia por conceptos y no por el orden cronológico de las clases. El recorrido real de la cursada se conserva en `bitacora.md`.

# Fundamentos del desarrollo frontend

## Qué es el frontend

El **frontend** es la parte de una aplicación con la que la persona usuaria interactúa directamente. En una aplicación web comprende la interfaz que el navegador presenta y el comportamiento asociado a esa interfaz: contenido, navegación, controles, formularios, respuestas visuales e interacción.

El frontend no se limita a “lo que se ve”. También incluye la lógica que se ejecuta del lado del cliente para reaccionar a eventos, validar entradas, actualizar la interfaz, comunicarse con servicios externos y administrar el estado necesario para la experiencia de uso.

En una aplicación web moderna, tres tecnologías forman la base del frontend:

| Tecnología | Responsabilidad principal |
|---|---|
| **HTML** | Define el contenido, la estructura y la semántica del documento. |
| **CSS** | Define la presentación visual y el layout. |
| **JavaScript** | Incorpora comportamiento, lógica e interactividad. |

Estas responsabilidades se relacionan, pero conviene mantenerlas conceptualmente separadas. Una estructura HTML clara facilita aplicar estilos con CSS y comportamiento con JavaScript sin convertir el documento en una mezcla difícil de mantener.

## Herramientas y abstracciones del ecosistema

Sobre HTML, CSS y JavaScript existen herramientas que permiten desarrollar interfaces complejas con mayor organización.

Una **biblioteca** ofrece funcionalidades que el código de la aplicación puede utilizar. Una **framework** proporciona una estructura más amplia para construir la aplicación y establece convenciones sobre cómo organizar distintas partes del sistema.

Dos ejemplos mencionados en la materia son:

- **React**: biblioteca orientada a la construcción de interfaces de usuario mediante componentes.
- **Angular**: framework para construir aplicaciones web basado en componentes y con herramientas integradas para resolver necesidades como enrutamiento, formularios, inyección de dependencias y comunicación con servicios.

La materia se concentrará posteriormente en Angular. En esta primera etapa, estos nombres funcionan principalmente como panorama del ecosistema; sus conceptos específicos se desarrollarán cuando aparezcan en la cursada.

---

# HTML

## Qué es HTML

**HTML (HyperText Markup Language)** es el lenguaje de marcado estándar utilizado para describir la estructura y el significado del contenido de un documento web.

No es un lenguaje de programación de propósito general: HTML es un lenguaje **declarativo de marcado**. En lugar de expresar algoritmos mediante instrucciones, declara qué representa cada parte del contenido mediante elementos.

Por ejemplo:

```html
<h1>Noticias</h1>
<p>Últimas novedades del proyecto.</p>
```

El navegador interpreta ese marcado como un encabezado principal seguido de un párrafo.

HTML constituye el “esqueleto” estructural del documento, pero su función no es únicamente visual. Un marcado bien elegido también comunica significado a navegadores, tecnologías de asistencia, motores de búsqueda y código que procese el documento.

## Hipertexto y marcado

El nombre HTML combina dos ideas:

- **HyperText**: documentos que pueden relacionarse entre sí mediante enlaces.
- **Markup**: contenido anotado mediante marcas que describen su estructura y significado.

Las marcas de HTML se expresan mediante **etiquetas**, que forman elementos.

```html
<p>Este contenido pertenece a un párrafo.</p>
```

Aquí:

- `<p>` es la etiqueta de apertura;
- `Este contenido pertenece a un párrafo.` es el contenido;
- `</p>` es la etiqueta de cierre;
- el conjunto completo constituye un elemento `<p>`.

## Elementos, etiquetas y contenido

Es útil distinguir **etiqueta** de **elemento**.

Una etiqueta es la sintaxis escrita entre `<` y `>`. Un elemento es la estructura completa representada por esa sintaxis, que puede incluir etiqueta de apertura, atributos, contenido y etiqueta de cierre.

```html
<a href="/contacto">Contacto</a>
```

En este caso:

- `<a href="/contacto">` es la etiqueta de apertura;
- `href="/contacto"` es un atributo;
- `Contacto` es el contenido;
- `</a>` es la etiqueta de cierre;
- todo el conjunto es el elemento de enlace.

Muchos elementos poseen apertura y cierre, pero HTML también define **elementos vacíos** (*void elements*) que no contienen nodos hijos y no utilizan etiqueta de cierre, como:

```html
<img src="logo.png" alt="Logo de la organización">
```

Por eso no debe asumirse que toda etiqueta HTML posee necesariamente una pareja de cierre.

## Estructura jerárquica y árbol del documento

Los elementos HTML se anidan unos dentro de otros y forman una estructura jerárquica.

```html
<main>
  <h1>Productos</h1>
  <article>
    <h2>Producto destacado</h2>
    <p>Descripción del producto.</p>
  </article>
</main>
```

En esta estructura:

- `main` contiene a `h1` y `article`;
- `h1` y `article` son **hermanos**, porque comparten el mismo padre;
- `article` es padre de `h2` y `p`;
- `h2` y `p` son hermanos.

Esta relación puede representarse como un árbol:

```mermaid
graph TD
    main[main]
    h1[h1]
    article[article]
    h2[h2]
    p[p]

    main --> h1
    main --> article
    article --> h2
    article --> p
```

El navegador transforma el documento HTML en una representación en memoria que posteriormente podrá manipularse desde JavaScript: el **DOM (Document Object Model)**. El DOM se estudiará con mayor profundidad cuando la materia avance sobre JavaScript y manipulación de interfaces.

## Estructura básica de un documento HTML

Una base moderna mínima puede escribirse así:

```html
<!doctype html>
<html lang="es">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi aplicación</title>
  </head>
  <body>
    <h1>Contenido principal</h1>
    <p>Primer documento HTML.</p>
  </body>
</html>
```

### `<!doctype html>`

Declara que el documento debe interpretarse como HTML moderno. Aunque históricamente los *doctypes* estuvieron asociados a definiciones concretas del lenguaje, en HTML actual `<!doctype html>` cumple principalmente la función de hacer que el navegador utilice su modo de renderizado estándar.

### `<html>`

Es el elemento raíz del documento. El resto de los elementos HTML son descendientes suyos.

El atributo `lang` identifica el idioma principal del documento:

```html
<html lang="es">
```

Esta información es relevante, entre otras cosas, para tecnologías de asistencia y para herramientas que procesan el contenido.

### `<head>`

Contiene metadatos y recursos asociados al documento, no el contenido principal que se presenta dentro de la página.

Entre sus usos habituales se encuentran:

- establecer el título del documento con `<title>`;
- declarar la codificación con `<meta charset="UTF-8">`;
- añadir metadatos;
- enlazar hojas de estilo;
- relacionar iconos u otros recursos;
- cargar determinados scripts.

Ejemplo:

```html
<head>
  <meta charset="UTF-8">
  <title>Catálogo</title>
  <link rel="stylesheet" href="styles.css">
</head>
```

### `<body>`

Representa el contenido del documento: encabezados, párrafos, navegación, imágenes, formularios, secciones y demás elementos que forman la página.

```html
<body>
  <h1>Catálogo</h1>
  <p>Productos disponibles.</p>
</body>
```

## Cómo procesa el navegador el HTML

El navegador recibe el código fuente HTML como una secuencia y lo **parsea** para construir el DOM.

Como modelo inicial resulta útil pensar que el parser avanza siguiendo el orden del documento. Sin embargo, no debe interpretarse esto como la regla informal de que “cualquier etiqueta de cierre puede ponerse en cualquier lugar”. HTML posee reglas precisas de anidamiento y cierre.

Los navegadores pueden corregir automáticamente ciertos errores de marcado para poder mostrar una página, pero que el navegador produzca algún resultado no significa que el HTML sea correcto.

Por ejemplo, esta estructura es clara y correctamente anidada:

```html
<article>
  <h2>Título</h2>
  <p>Contenido.</p>
</article>
```

Un documento bien estructurado reduce resultados inesperados y facilita accesibilidad, estilos, mantenimiento y manipulación mediante JavaScript.

---

# Semántica en HTML

## Qué significa semántica

La **semántica** describe el significado de un elemento, no simplemente su apariencia.

Por ejemplo:

```html
<nav>
  ...
</nav>
```

comunica que el contenido constituye una zona de navegación.

En cambio:

```html
<div>
  ...
</div>
```

define un contenedor genérico sin expresar por sí mismo qué función cumple ese bloque.

HTML incluye elementos estructurales como:

- `<header>`;
- `<nav>`;
- `<main>`;
- `<section>`;
- `<article>`;
- `<aside>`;
- `<footer>`.

También existen muchos otros elementos cuyo significado es semántico aunque no pertenezcan específicamente al grupo de elementos estructurales, como `<a>`, `<button>`, `<img>`, `<form>` o los encabezados `<h1>` a `<h6>`.

Por lo tanto, “semántico” no significa simplemente “tener un nombre que describe una zona de la página”; se refiere a utilizar el elemento que expresa correctamente el significado y propósito del contenido.

## Semántica frente a contenedores genéricos

`<div>` y `<span>` son contenedores genéricos útiles cuando no existe un elemento con una semántica más apropiada.

Un sitio podría construirse visualmente con numerosos `<div>` y CSS, pero hacerlo de manera indiscriminada elimina información estructural que HTML ya puede expresar.

Por ejemplo:

```html
<div class="nav">
  <a href="/">Inicio</a>
  <a href="/contacto">Contacto</a>
</div>
```

puede sustituirse, cuando corresponde conceptualmente, por:

```html
<nav>
  <a href="/">Inicio</a>
  <a href="/contacto">Contacto</a>
</nav>
```

Ambos bloques pueden verse idénticos después de aplicar CSS, pero el segundo comunica además que se trata de navegación.

## Por qué importa el HTML semántico

### Mantenibilidad

Un elemento adecuado permite comprender más rápidamente la intención del código.

```html
<header>...</header>
<main>...</main>
<footer>...</footer>
```

expresa más información que una sucesión de contenedores genéricos sin nombres claros.

Esto cobra especial importancia cuando un proyecto debe ser modificado meses después o pasa de una persona a otra.

### Accesibilidad

Muchos elementos HTML aportan semántica que las tecnologías de asistencia pueden utilizar.

Los lectores de pantalla y otras herramientas pueden beneficiarse de:

- regiones estructurales;
- niveles correctos de encabezados;
- enlaces reales;
- botones reales;
- etiquetas asociadas a controles de formulario;
- texto alternativo apropiado para imágenes.

La accesibilidad no depende solamente de utilizar etiquetas estructurales, pero un HTML semántico correcto proporciona una base importante.

### SEO

La estructura y la semántica del HTML ayudan a los motores de búsqueda a interpretar el contenido.

Sin embargo, utilizar `<main>`, `<article>` o `<footer>` no garantiza por sí mismo una posición determinada en los resultados. El **SEO (Search Engine Optimization)** comprende un conjunto mucho mayor de prácticas relacionadas con contenido, rastreo, indexación, rendimiento, metadatos, enlaces y otros factores.

Por eso, la relación correcta es:

> El HTML semántico contribuye a que el contenido sea interpretable y forma parte de una buena base técnica para SEO; no constituye por sí solo una estrategia completa de posicionamiento.

---

# Metadatos

Los **metadatos** son información que describe o complementa otros datos.

En un documento HTML, el `<head>` actúa como contenedor de buena parte de la información asociada al documento.

Ejemplos:

```html
<meta charset="UTF-8">
<meta name="description" content="Catálogo de productos tecnológicos">
```

El primer elemento define la codificación de caracteres. El segundo aporta una descripción del documento.

No todos los metadatos de interés se expresan mediante `<meta>`. Por ejemplo:

```html
<title>Catálogo</title>
<link rel="stylesheet" href="styles.css">
```

también forman parte de la información y recursos asociados al documento dentro de `<head>`.

El idioma principal, por otra parte, se declara normalmente mediante el atributo `lang` del elemento raíz:

```html
<html lang="es">
```

---

# Atributos HTML

## Qué es un atributo

Los **atributos** agregan información a un elemento o configuran determinadas características de su comportamiento.

Se escriben normalmente en la etiqueta de apertura.

```html
<a href="/perfil" class="enlace-principal">Mi perfil</a>
```

Aquí:

- `href` indica el destino del enlace;
- `class` asigna una clase que puede utilizarse desde CSS o JavaScript.

La forma más habitual es:

```text
nombre="valor"
```

pero no todos los atributos necesitan un valor textual explícito.

## Atributos booleanos

HTML define atributos booleanos cuya presencia representa el valor verdadero.

Por ejemplo:

```html
<input type="text" disabled>
```

La presencia de `disabled` deshabilita el control. Por eso, aunque el modelo “nombre–valor” es útil para muchos atributos, no es una regla universal de la sintaxis HTML.

## Atributos globales y específicos

Algunos atributos pueden aplicarse a gran cantidad de elementos, como:

- `id`;
- `class`;
- `title`;
- `lang`;
- `hidden`.

Otros pertenecen a elementos concretos:

```html
<a href="/inicio">Inicio</a>
<img src="foto.jpg" alt="Equipo de trabajo">
```

`href` tiene sentido para el enlace y `src`/`alt` para la imagen.

## `class` y separación entre estructura y presentación

El atributo `class` permite identificar uno o varios elementos para aplicar reglas CSS o seleccionarlos desde JavaScript.

```html
<p class="destacado">Contenido importante</p>
```

```css
.destacado {
  font-weight: bold;
}
```

HTML también permite utilizar el atributo `style`:

```html
<p style="font-weight: bold">Contenido importante</p>
```

Este código es válido, pero en proyectos mantenibles suele preferirse separar la estructura HTML de las reglas de presentación, concentrando los estilos en CSS. Esto facilita reutilización, consistencia y mantenimiento.

---

# JavaScript

## Qué es JavaScript

**JavaScript** es un lenguaje de programación de propósito general estandarizado mediante **ECMAScript**. Nació vinculado al navegador y al desarrollo de páginas web interactivas, pero actualmente también se ejecuta fuera del navegador mediante entornos como Node.js.

En frontend permite, entre otras cosas:

- reaccionar a acciones del usuario;
- modificar contenido y estado de la interfaz;
- validar y procesar datos;
- trabajar con eventos;
- comunicarse con servicios;
- coordinar operaciones asincrónicas;
- manipular el DOM.

HTML aporta principalmente estructura y semántica, CSS presentación y JavaScript comportamiento y lógica.

## Breve evolución

JavaScript apareció en 1995 en Netscape y fue creado por Brendan Eich. Antes de adoptar su nombre actual pasó por los nombres Mocha y LiveScript.

Posteriormente comenzó su estandarización mediante Ecma International. El lenguaje estandarizado se denomina **ECMAScript** y se especifica en ECMA-262.

**ECMAScript 2015 (ES6)** incorporó numerosas características fundamentales del JavaScript moderno, entre ellas `let`, `const` y las funciones flecha.

La aparición de **Node.js** extendió fuertemente el uso de JavaScript fuera del navegador.

## Lenguaje de alto nivel, dinámico y multiparadigma

JavaScript es un lenguaje de **alto nivel**: abstrae detalles como la administración manual de memoria y ofrece construcciones apropiadas para trabajar con conceptos de mayor nivel.

También es **multiparadigma** y permite combinar programación:

- imperativa;
- funcional;
- orientada a objetos;
- dirigida por eventos.

### Tipado dinámico

El tipo pertenece al valor, no queda fijado permanentemente a una variable.

```javascript
let dato = 10;
dato = "diez";
dato = true;
```

Una misma variable puede referenciar valores de tipos distintos durante la ejecución.

### Coerción de tipos

JavaScript puede realizar conversiones implícitas según la operación:

```javascript
console.log("1" + 1); // "11"
```

En este caso el número se convierte implícitamente en texto y `+` produce concatenación.

Esta flexibilidad suele relacionarse con la descripción de JavaScript como un lenguaje de tipado débil, aunque “fuerte” y “débil” no poseen una única definición formal universal. Resulta más útil comprender las reglas concretas de **coerción**.

También pueden realizarse conversiones explícitas:

```javascript
Number("42");  // 42
String(42);    // "42"
Boolean(1);    // true
```

## Template literals

Los **template literals** son cadenas delimitadas por backticks (`` ` ``) que permiten interpolar expresiones y escribir texto en varias líneas.

```javascript
const nombre = "Marta";
const edad = 35;

console.log(`Nombre: ${nombre}. Edad: ${edad}.`);
```

La expresión incluida dentro de `${...}` se evalúa primero y su resultado se incorpora a la cadena.

```javascript
const a = 3;
const b = 5;

console.log(`Resultado: ${a + b}`); // "Resultado: 8"
```

En cambio:

```javascript
console.log(`${a} + ${b}`); // "3 + 5"
```

el operador `+` está fuera de la expresión interpolada y forma parte del texto literal.

Los template literals también admiten saltos de línea directamente:

```javascript
const mensaje = `Primera línea
Segunda línea`;
```

No debe entenderse que “todo lo que está dentro se convierte antes a string”. El texto literal forma una cadena, mientras que las expresiones `${...}` se evalúan como JavaScript y luego sus resultados se convierten según las reglas de interpolación.

### Objetos dentro de un template literal

Si se interpola directamente un objeto común:

```javascript
const persona = { nombre: "Ana" };

console.log(`${persona}`);
```

la conversión a string suele producir:

```text
[object Object]
```

Esto ocurre porque se aplica la conversión ordinaria del objeto a texto. Para obtener una representación JSON puede utilizarse `JSON.stringify()`:

```javascript
console.log(JSON.stringify(persona));
// '{"nombre":"Ana"}'
```

---

# JSON

## Qué es JSON

**JSON (JavaScript Object Notation)** es un formato textual para representar e intercambiar datos estructurados.

Aunque su sintaxis está inspirada en los objetos literales de JavaScript, **JSON no es un tipo de dato JavaScript ni es lo mismo que un objeto JavaScript**.

Ejemplo JSON:

```json
{
  "nombre": "Ana",
  "edad": 35,
  "activo": true
}
```

Su naturaleza textual facilita el intercambio de información entre sistemas y lenguajes diferentes, razón por la que aparece con frecuencia en APIs web.

## Objeto literal y JSON

Un objeto literal JavaScript puede escribirse así:

```javascript
const persona = {
  nombre: "Ana",
  edad: 35
};
```

Esto crea un objeto real dentro del programa.

Una representación JSON equivalente sería texto:

```json
{
  "nombre": "Ana",
  "edad": 35
}
```

La sintaxis se parece, pero sus reglas no son idénticas. Por ejemplo, en JSON los nombres de las propiedades deben escribirse entre comillas dobles.

## `JSON.stringify()`

`JSON.stringify()` serializa un valor JavaScript a una cadena en formato JSON cuando ese valor puede representarse mediante JSON.

```javascript
const persona = {
  nombre: "Ana",
  edad: 35
};

const texto = JSON.stringify(persona);

console.log(typeof texto); // "string"
console.log(texto);        // '{"nombre":"Ana","edad":35}'
```

No es correcto pensar que simplemente “pone comillas a todo”. La serialización respeta los tipos compatibles con JSON: los números continúan representándose como números, los booleanos como booleanos y las cadenas como cadenas.

Además, no todo valor JavaScript tiene una representación JSON directa. Por ejemplo, propiedades cuyo valor es `undefined`, una función o un `Symbol` pueden omitirse durante la serialización.

## `JSON.parse()`

`JSON.parse()` realiza el camino inverso: analiza una cadena JSON válida y produce el valor JavaScript correspondiente.

```javascript
const texto = '{"nombre":"Ana","edad":35}';
const persona = JSON.parse(texto);

console.log(persona.nombre); // "Ana"
console.log(typeof persona); // "object"
```

Por lo tanto:

```text
valor JavaScript
      │
      │ JSON.stringify()
      ▼
texto JSON
      │
      │ JSON.parse()
      ▼
valor JavaScript
```

Este mecanismo es especialmente importante cuando una aplicación recibe o envía información mediante APIs.


## ECMAScript, motor y entorno

Conviene separar tres conceptos.

### ECMAScript

Es la especificación que define el núcleo del lenguaje.

### Motor de JavaScript

Es el software que implementa ECMAScript y ejecuta el código.

Entre los motores conocidos se encuentran:

- **V8**, utilizado por Chrome y Node.js;
- **SpiderMonkey**, utilizado por Firefox;
- **JavaScriptCore**, utilizado por Safari.

Los motores modernos no se limitan a “interpretar línea por línea”: utilizan análisis, interpretación y **compilación JIT (Just-In-Time)** para optimizar la ejecución.

Por eso, afirmar simplemente que JavaScript “es interpretado y no compilado” es una simplificación. Desde el punto de vista de quien desarrolla no suele existir un paso manual de compilación previo para ejecutar JavaScript común, pero internamente los motores modernos sí compilan y optimizan código.

### Entorno anfitrión

El motor implementa el lenguaje; el entorno proporciona APIs adicionales.

En un navegador aparecen, por ejemplo:

- DOM;
- eventos;
- `fetch`;
- temporizadores;
- almacenamiento web.

Node.js proporciona otras APIs para archivos, procesos, red y servidores.

## Script y algoritmo

Un **algoritmo** describe de manera abstracta un procedimiento para resolver un problema. Puede expresarse con lenguaje natural, pseudocódigo, diagramas o código.

Un **script** es código concreto escrito en un lenguaje y ejecutable dentro de un entorno.

Por lo tanto, un script puede implementar uno o varios algoritmos, pero ambos conceptos no son equivalentes.

---

# Variables y bindings

## `let`

`let` declara un binding con **alcance de bloque** y permite reasignarlo.

```javascript
let contador = 1;
contador = 2;
```

No permite redeclarar el mismo identificador dentro del mismo ámbito:

```javascript
let contador = 1;
// let contador = 2; // SyntaxError
```

## `const`

`const` también tiene alcance de bloque, pero exige inicialización y no permite reasignar el binding.

```javascript
const PI = 3.14159;
// PI = 3; // TypeError
```

Esto no vuelve inmutable al valor si se trata de un objeto:

```javascript
const usuario = {
  nombre: "Ana"
};

usuario.nombre = "Lucía"; // válido
usuario.edad = 30;        // válido

// usuario = {};          // TypeError
```

La restricción de `const` afecta a la reasignación de la variable, no a todas las mutaciones internas del valor.

Como regla general para código moderno:

- usar `const` cuando no haga falta reasignar;
- usar `let` cuando sí;
- evitar `var` salvo necesidad concreta o código legado.

## `var`

`var` es anterior a `let` y `const` y posee diferencias importantes:

- tiene alcance de función, no de bloque;
- permite redeclaración;
- posee comportamientos históricos de *hoisting* que pueden resultar poco intuitivos.

```javascript
function ejemplo() {
  if (true) {
    var mensaje = "hola";
  }

  console.log(mensaje); // "hola"
}
```

Con `let`, el binding queda limitado al bloque:

```javascript
function ejemplo() {
  if (true) {
    let mensaje = "hola";
  }

  // console.log(mensaje); // ReferenceError
}
```

### Hoisting de `var`

Una declaración `var` pertenece al ámbito completo de la función aunque la asignación permanezca en su posición original.

```javascript
function ejemplo(condicion) {
  if (condicion) {
    var valor = 10;
  }

  console.log(valor);
}

ejemplo(false); // undefined
```

La declaración existe en el ámbito de la función, pero como la rama del `if` no se ejecutó, nunca ocurrió `valor = 10`.

## No crear variables implícitas

Código como:

```javascript
resultado = 10;
```

puede crear una propiedad global accidental en scripts clásicos no estrictos.

No debe utilizarse como forma de declaración.

En modo estricto y en módulos JavaScript produce un `ReferenceError`. Los bindings deben declararse explícitamente.

---

# Scope o alcance

El **scope** determina en qué parte del programa puede resolverse un identificador.

JavaScript posee:

- alcance global;
- alcance de módulo;
- alcance de función;
- alcance de bloque.

`let` y `const` respetan alcance de bloque:

```javascript
if (true) {
  const mensaje = "visible aquí";
}

// console.log(mensaje); // ReferenceError
```

`var` no queda limitado por un bloque común:

```javascript
if (true) {
  var mensaje = "visible fuera del if";
}

console.log(mensaje);
```

Una función sí crea un ámbito para `var`:

```javascript
function ejemplo() {
  var local = 10;
}

// console.log(local); // ReferenceError
```

Los ámbitos se anidan: el código interno puede acceder a bindings externos disponibles, pero el código externo no puede acceder directamente a bindings locales internos.

---

# Tipos de datos

## Primitivos

JavaScript define siete tipos primitivos:

| Tipo | Ejemplo |
|---|---|
| `string` | `"hola"` |
| `number` | `42`, `3.14` |
| `bigint` | `123n` |
| `boolean` | `true`, `false` |
| `undefined` | `undefined` |
| `symbol` | `Symbol("id")` |
| `null` | `null` |

Los primitivos son **inmutables**: una operación no modifica internamente el valor primitivo original; una reasignación hace que el binding pase a contener otro valor.

### `null`

`null` representa intencionalmente ausencia de valor:

```javascript
let seleccion = null;
```

Es un valor primitivo, aunque por una particularidad histórica:

```javascript
typeof null; // "object"
```

Ese resultado no significa que `null` sea realmente un objeto.

### `undefined`

`undefined` aparece habitualmente cuando un binding o una propiedad no posee otro valor definido.

```javascript
let resultado;

console.log(resultado); // undefined
```

Una distinción útil:

- `null`: ausencia establecida deliberadamente;
- `undefined`: valor todavía no definido o inexistente en ese acceso.

## Valores truthy y falsy

En condiciones, JavaScript puede convertir valores a booleanos.

Entre los valores **falsy** se encuentran:

```text
false
0
-0
0n
""
null
undefined
NaN
```

Por ejemplo:

```javascript
const dato = null;

if (dato) {
  // no se ejecuta
}
```

---

# Objetos

Los valores no primitivos pertenecen al tipo `object`.

```javascript
const vendedor = {
  nombre: "Carlos",
  apellido: "Sánchez",
  edad: 56
};
```

Cada propiedad asocia una clave con un valor.

```text
nombre   → "Carlos"
apellido → "Sánchez"
edad     → 56
```

Las propiedades pueden almacenar primitivas, arrays, otros objetos o funciones.

## Acceso y modificación

```javascript
console.log(vendedor.nombre);

vendedor.nombre = "Juan";
vendedor.email = "juan@example.com";
```

Esto es compatible con `const` porque se modifica el objeto, no se reasigna la variable `vendedor`.

---

# Estructuras de control

## Condicional `if`

`if` permite ejecutar un bloque cuando una condición resulta verdadera.

```javascript
const edad = 20;

if (edad >= 18) {
  console.log("Es mayor de edad");
}
```

Puede complementarse con `else`:

```javascript
if (edad >= 18) {
  console.log("Mayor");
} else {
  console.log("Menor");
}
```

## Operador condicional ternario

El operador ternario expresa una selección entre dos expresiones:

```javascript
const resultado = edad >= 18
  ? "Mayor"
  : "Menor";
```

Su forma general es:

```text
condición ? expresiónSiVerdadero : expresiónSiFalso
```

Es útil para decisiones breves. Cuando la lógica contiene múltiples pasos o ramas complejas, un `if` suele ser más legible.

## Bucles

### `for`

`for` es apropiado cuando la iteración se controla mediante inicialización, condición y actualización.

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

### `while`

`while` repite un bloque mientras la condición sea verdadera.

```javascript
let i = 0;

while (i < 5) {
  console.log(i);
  i++;
}
```

### `do...while`

`do...while` evalúa la condición después de ejecutar el cuerpo, por lo que este se ejecuta al menos una vez.

```javascript
let i = 0;

do {
  console.log(i);
  i++;
} while (i < 5);
```

Los métodos de arrays como `forEach()`, `map()` o `filter()` no reemplazan conceptualmente a todos los bucles, pero ofrecen abstracciones expresivas para operaciones habituales sobre colecciones.

---

# DOM

## Qué es el DOM

El **DOM (Document Object Model)** es una representación programática de un documento HTML como una estructura de nodos.

Por ejemplo, a partir de:

```html
<body>
  <main>
    <h1>Frontend</h1>
    <p>Introducción al DOM</p>
  </main>
</body>
```

puede pensarse una jerarquía como:

```mermaid
graph TD
    A[Document] --> B[html]
    B --> C[head]
    B --> D[body]
    D --> E[main]
    E --> F[h1]
    E --> G[p]
```

JavaScript puede interactuar con esa representación para:

- consultar elementos;
- cambiar contenido;
- modificar atributos;
- cambiar clases o estilos;
- crear o eliminar nodos;
- reaccionar a eventos.

El DOM no es el texto HTML original ni forma parte del núcleo de ECMAScript: es una API proporcionada por el entorno del navegador.

---

# Eventos

## Concepto

Un **evento** representa algo que ocurre en el entorno y que el programa puede observar: un clic, una tecla presionada, un cambio en un campo, la carga de un recurso, entre muchos otros.

El patrón general es:

```text
ocurre un evento
      ↓
el navegador lo detecta
      ↓
se ejecuta una función asociada
```

Por ejemplo:

```javascript
const boton = document.querySelector("#guardar");

boton.addEventListener("click", () => {
  console.log("Se hizo clic");
});
```

Aquí:

- `"click"` es el tipo de evento;
- la función entregada a `addEventListener()` es el callback que se ejecutará cuando ocurra.

## Nombre del evento y manejador

Conviene distinguir el nombre del evento de propiedades históricas como `onclick`.

Con `addEventListener()` se utiliza:

```javascript
elemento.addEventListener("click", callback);
```

no:

```javascript
elemento.addEventListener("onclick", callback);
```

`click` es el tipo de evento. `onclick` es una propiedad para asignar un manejador:

```javascript
boton.onclick = () => {
  console.log("clic");
};
```

En código moderno, `addEventListener()` suele ser preferible porque permite registrar múltiples listeners y ofrece más opciones de control.

Otros eventos frecuentes son:

```text
keydown
input
change
submit
focus
blur
load
mouseover
```

---

# Manejo de errores

## `try...catch`

`try...catch` permite capturar excepciones que ocurren durante la ejecución.

```javascript
try {
  JSON.parse("texto que no es JSON");
} catch (error) {
  console.error("No se pudo procesar el JSON");
}
```

El bloque `try` contiene el código que puede lanzar una excepción.

Si ocurre una excepción capturable, la ejecución salta al `catch`.

El objeto recibido en `catch` permite inspeccionar información sobre el error:

```javascript
try {
  JSON.parse("{");
} catch (error) {
  console.log(error.name);
  console.log(error.message);
}
```

## `finally`

Puede agregarse un bloque `finally`:

```javascript
try {
  console.log("Intento");
} catch (error) {
  console.error(error);
} finally {
  console.log("Esto se ejecuta al finalizar");
}
```

`finally` se ejecuta tanto si el `try` completa normalmente como si se produce una excepción capturada.

## Qué no hace `try...catch`

No debe entenderse como un mecanismo que vuelve seguro cualquier código o evita que “el programa explote” ante cualquier problema.

`try...catch` trabaja con **excepciones lanzadas durante la ejecución** dentro de su alcance. No corrige errores lógicos y existen situaciones asincrónicas en las que un `try...catch` externo no captura automáticamente un error producido posteriormente.

El tratamiento detallado de errores asincrónicos se relacionará más adelante con promesas y `async`/`await`.

---

# Arrays

## Qué es un array

Un **array** es un objeto especializado de JavaScript para representar colecciones ordenadas de valores.

```javascript
const frutas = ["manzana", "pera", "banana"];
```

Sus características básicas son:

- mantiene un orden;
- cada elemento posee un índice numérico;
- el primer índice es `0`;
- su longitud se consulta mediante `length`;
- puede contener valores de distintos tipos;
- es mutable: determinados métodos pueden modificar su contenido.

```javascript
console.log(frutas[0]);     // "manzana"
console.log(frutas.length); // 3
```

Aunque conceptualmente puede pensarse como una colección o secuencia, JavaScript no posee un tipo incorporado denominado `List` equivalente a las listas de otros lenguajes. Conviene estudiar `Array` según su propio comportamiento en JavaScript.

## Creación

La forma literal es la más habitual:

```javascript
const numeros = [10, 20, 30];
```

También existe el constructor:

```javascript
const numeros = new Array(10, 20, 30);
```

Debe tenerse cuidado con una llamada como:

```javascript
const valores = new Array(5);
```

Esto no crea `[5]`: crea un array con `length === 5` y cinco posiciones vacías.

En código habitual, la sintaxis literal suele ser más clara.

## Detección de arrays

Como los arrays son objetos:

```javascript
typeof []; // "object"
```

`typeof` no permite distinguir un array de un objeto común.

Para verificar específicamente si un valor es un array se utiliza:

```javascript
Array.isArray([1, 2, 3]); // true
Array.isArray({});        // false
```

## Igualdad y referencias

Dos arrays creados por separado son objetos distintos aunque contengan los mismos elementos:

```javascript
const a = [1, 2, 3];
const b = [1, 2, 3];

console.log(a === b); // false
```

En cambio:

```javascript
const a = [1, 2, 3];
const b = a;

console.log(a === b); // true
```

`a` y `b` referencian el mismo array.

---

## Métodos que consultan o crean resultados sin modificar el array original

Es importante distinguir los métodos que **mutan** el array receptor de los que producen información o nuevos arrays.

### `filter()`

`filter()` recorre el array y devuelve un **nuevo array** con todos los elementos que cumplen una condición.

```javascript
const frutas = ["manzana", "pera", "banana", "pera"];

const peras = frutas.filter(fruta => fruta === "pera");

console.log(peras);  // ["pera", "pera"]
console.log(frutas); // no se modifica
```

También puede filtrarse por propiedades de objetos:

```javascript
const materias = [
  { nombre: "Frontend", activa: true },
  { nombre: "Backend", activa: false },
  { nombre: "Datos", activa: true }
];

const activas = materias.filter(materia => materia.activa);
```

`filter()` no “elimina” elementos del array original. Puede utilizarse para construir un nuevo array que excluya determinados elementos:

```javascript
const sinPeras = frutas.filter(fruta => fruta !== "pera");
```

pero `frutas` continúa intacto.

### `find()`

`find()` devuelve el **primer elemento** que satisface la condición.

```javascript
const numeros = [2, 7, 12, 20];

const encontrado = numeros.find(numero => numero > 10);

console.log(encontrado); // 12
```

Si no encuentra ninguno, devuelve `undefined`.

Una diferencia conceptual importante:

- `filter()` busca todas las coincidencias y devuelve un array;
- `find()` se detiene cuando encuentra la primera coincidencia y devuelve ese elemento.

Cuando solo se necesita una coincidencia, `find()` expresa mejor la intención y puede evitar recorrer innecesariamente el resto del array.

### `findIndex()`

`findIndex()` devuelve el índice del primer elemento que satisface la condición.

```javascript
const numeros = [2, 7, 12, 20];

const indice = numeros.findIndex(numero => numero > 10);

console.log(indice); // 2
```

Si no existe coincidencia devuelve `-1`.

### `some()`

`some()` responde si **al menos un elemento** cumple la condición.

```javascript
const numeros = [2, 4, 7];

console.log(numeros.some(numero => numero % 2 !== 0)); // true
```

Devuelve un booleano y puede finalizar tan pronto encuentra una coincidencia.

### `every()`

`every()` responde si **todos los elementos** cumplen la condición.

```javascript
const numeros = [2, 4, 8];

console.log(numeros.every(numero => numero % 2 === 0)); // true
```

Si algún elemento no satisface la condición, puede finalizar la búsqueda inmediatamente.

### `slice()`

`slice()` devuelve una **copia superficial** de una porción del array y no modifica el original.

```javascript
const letras = ["a", "b", "c", "d", "e", "f"];

const parte = letras.slice(2, 5);

console.log(parte);  // ["c", "d", "e"]
console.log(letras); // sin cambios
```

El índice inicial se incluye y el índice final se excluye:

```text
slice(inicio, fin)
      incluido
              excluido
```

### `concat()`

`concat()` combina valores o arrays y devuelve un nuevo array.

```javascript
const a = [1, 2];
const b = [3, 4];

const combinado = a.concat(b);

console.log(combinado); // [1, 2, 3, 4]
console.log(a);         // [1, 2]
```

### `forEach()`

`forEach()` ejecuta una función una vez por cada elemento.

```javascript
const frutas = ["manzana", "pera", "banana"];

frutas.forEach(fruta => {
  console.log(fruta);
});
```

El callback puede recibir tres argumentos:

```javascript
frutas.forEach((elemento, indice, array) => {
  console.log(elemento);
  console.log(indice);
  console.log(array);
});
```

Por convención:

1. primer parámetro: elemento actual;
2. segundo: índice;
3. tercero: array recorrido.

`forEach()` no crea automáticamente un nuevo array transformado. Su valor de retorno es `undefined`.

Esto no significa que sea imposible modificar datos desde su callback. Por ejemplo:

```javascript
const numeros = [1, 2, 3];

numeros.forEach((numero, indice, array) => {
  array[indice] = numero * 2;
});

console.log(numeros); // [2, 4, 6]
```

La mutación ocurre porque el callback modifica explícitamente el array original.

Para producir una colección transformada suele ser más apropiado `map()`.

### `map()`

`map()` devuelve un nuevo array aplicando una transformación a cada elemento.

```javascript
const numeros = [1, 2, 3];

const dobles = numeros.map(numero => numero * 2);

console.log(dobles);  // [2, 4, 6]
console.log(numeros); // [1, 2, 3]
```

La diferencia central frente a `forEach()` es de intención y retorno:

- `forEach()` ejecuta una acción por elemento y devuelve `undefined`;
- `map()` construye y devuelve un nuevo array con los resultados.

---

## Métodos que modifican el array original

### `push()`

Agrega uno o más elementos al final y devuelve la nueva longitud.

```javascript
const frutas = ["manzana"];

const longitud = frutas.push("pera");

console.log(frutas);  // ["manzana", "pera"]
console.log(longitud); // 2
```

### `pop()`

Elimina y devuelve el último elemento.

```javascript
const frutas = ["manzana", "pera"];

const ultima = frutas.pop();

console.log(ultima);  // "pera"
console.log(frutas);  // ["manzana"]
```

### `shift()`

Elimina y devuelve el primer elemento.

```javascript
const frutas = ["manzana", "pera"];

const primera = frutas.shift();

console.log(primera); // "manzana"
console.log(frutas);  // ["pera"]
```

### `unshift()`

Agrega uno o más elementos al principio y devuelve la nueva longitud.

```javascript
const frutas = ["pera"];

frutas.unshift("manzana");

console.log(frutas); // ["manzana", "pera"]
```

### `fill()`

`fill()` reemplaza posiciones del array con un valor y **modifica el array original**.

```javascript
const valores = ["a", "b", "c", "d", "e"];

valores.fill("x", 1, 4);

console.log(valores);
// ["a", "x", "x", "x", "e"]
```

La forma general es:

```javascript
array.fill(valor, inicio, fin);
```

- `inicio` está incluido;
- `fin` está excluido;
- si se omiten índices, puede reemplazarse todo el array.

Además, `fill()` devuelve una referencia al mismo array modificado.

### `splice()`

`splice()` permite eliminar, insertar o reemplazar elementos **modificando el array original**.

Forma general:

```javascript
array.splice(indiceInicial, cantidadAEliminar, ...elementosNuevos);
```

#### Eliminar

```javascript
const numeros = [1, 2, 3, 4, 5];

const eliminados = numeros.splice(2, 1);

console.log(numeros);   // [1, 2, 4, 5]
console.log(eliminados); // [3]
```

#### Insertar sin eliminar

```javascript
const numeros = [1, 2, 3, 4, 5];

numeros.splice(2, 0, 99, 100);

console.log(numeros);
// [1, 2, 99, 100, 3, 4, 5]
```

#### Reemplazar

```javascript
const numeros = [1, 2, 3, 4, 5];

const eliminados = numeros.splice(2, 2, 99, 100);

console.log(numeros);
// [1, 2, 99, 100, 5]

console.log(eliminados);
// [3, 4]
```

La distinción es importante:

- modifica el array original;
- devuelve un nuevo array que contiene los elementos eliminados.

## `slice()` frente a `splice()`

Aunque sus nombres se parecen, sus comportamientos son muy distintos:

| Método | Modifica original | Resultado principal |
|---|---:|---|
| `slice()` | No | copia una porción |
| `splice()` | Sí | inserta/elimina/reemplaza y devuelve eliminados |

---

## Ordenamiento con `sort()`

`sort()` ordena el array **in place**, por lo que modifica el original.

```javascript
const frutas = ["pera", "banana", "manzana"];

frutas.sort();

console.log(frutas);
// ["banana", "manzana", "pera"]
```

### Ordenamiento numérico

El orden por defecto convierte los elementos a strings y los compara según sus valores UTF-16.

Por eso:

```javascript
const numeros = [2, 4, 10, 15, 22, 30];

numeros.sort();

console.log(numeros);
// [10, 15, 2, 22, 30, 4]
```

No es el orden matemático esperado.

Para ordenar números de forma ascendente:

```javascript
numeros.sort((a, b) => a - b);
```

Para orden descendente:

```javascript
numeros.sort((a, b) => b - a);
```

La función comparadora debe devolver:

- un número negativo si `a` debe aparecer antes que `b`;
- un número positivo si `a` debe aparecer después de `b`;
- `0` si ambos se consideran equivalentes para el ordenamiento.

### No asumir un algoritmo interno único

La especificación define el comportamiento observable de `sort()`, pero no obliga a utilizar un único algoritmo concreto ni garantiza una complejidad temporal fija.

Desde ECMAScript 2019 el ordenamiento debe ser **estable**: si dos elementos son equivalentes para la función comparadora, conservan entre sí su orden relativo previo.

Por lo tanto, no debe estudiarse `sort()` como sinónimo de Timsort ni asignársele una complejidad fija como propiedad del lenguaje.

### Ordenar sin modificar el original

En JavaScript moderno existe `toSorted()`:

```javascript
const originales = [3, 1, 2];
const ordenados = originales.toSorted((a, b) => a - b);

console.log(originales); // [3, 1, 2]
console.log(ordenados);  // [1, 2, 3]
```

También puede hacerse una copia antes de ordenar:

```javascript
const ordenados = [...originales].sort((a, b) => a - b);
```

---

## Mutabilidad e inmutabilidad práctica

Al trabajar con arrays conviene saber si una operación modifica la estructura original.

### Habitualmente no mutan

- `filter()`;
- `find()`;
- `findIndex()`;
- `some()`;
- `every()`;
- `slice()`;
- `concat()`;
- `map()`.

### Mutan

- `push()`;
- `pop()`;
- `shift()`;
- `unshift()`;
- `fill()`;
- `splice()`;
- `sort()`.

`forEach()` merece una distinción: el método no transforma por sí mismo el array ni devuelve uno nuevo, pero el callback puede realizar mutaciones explícitas.

Conocer esta diferencia ayuda a evitar cambios accidentales de estado y será especialmente importante al trabajar posteriormente con componentes y estado de interfaz.

# Funciones

Una **función** agrupa instrucciones reutilizables que pueden ejecutarse cuando la función es invocada.

```javascript
function saludar() {
  console.log("Hola");
}

saludar();
```

Las funciones pueden:

- recibir datos;
- realizar operaciones;
- producir efectos;
- devolver valores;
- almacenarse en variables o propiedades;
- pasarse como argumentos.

En JavaScript son valores de primera clase.

## Parámetros y argumentos

```javascript
function saludar(nombre) {
  console.log(`Hola ${nombre}`);
}

saludar("Ana");
```

- `nombre` es un **parámetro**;
- `"Ana"` es un **argumento**.

## Métodos

Cuando una función se almacena como propiedad de un objeto y se invoca a través de él, suele denominarse **método**.

```javascript
const vendedor = {
  nombre: "Carlos",

  vender() {
    console.log(`${this.nombre} vendió un producto`);
  }
};

vendedor.vender();
```

La diferencia entre función y método no depende de que exista o no un valor de retorno.

## Funciones tradicionales

```javascript
function sumar(a, b) {
  return a + b;
}
```

También pueden escribirse como expresión:

```javascript
const sumar = function (a, b) {
  return a + b;
};
```

## Funciones flecha

```javascript
const sumar = (a, b) => {
  return a + b;
};
```

Si el cuerpo es una única expresión:

```javascript
const sumar = (a, b) => a + b;
```

Las arrow functions no son solo una abreviatura de `function`.

### `this` léxico

Una función tradicional usada como método puede recibir `this` según cómo se invoca:

```javascript
const persona = {
  nombre: "Ana",

  mostrarNombre() {
    console.log(this.nombre);
  }
};
```

Una arrow function **no crea su propio `this`**: captura el `this` del contexto exterior.

```javascript
const persona = {
  nombre: "Ana",

  mostrarNombre: () => {
    console.log(this.nombre);
  }
};
```

No debe suponerse que en este segundo caso `this` sea `persona`.

La arrow puede acceder a datos del objeto mediante parámetros u otras referencias explícitas; la diferencia específica está en el comportamiento de `this`.

Las arrow functions tampoco pueden utilizarse como constructor con `new`.

---

## Retorno implícito en funciones flecha

Cuando una arrow function contiene una única expresión, puede omitir las llaves y la palabra `return`.

```javascript
const sumarDos = numero => numero + 2;

console.log(sumarDos(5)); // 7
```

Es equivalente, en cuanto al valor retornado, a:

```javascript
const sumarDos = numero => {
  return numero + 2;
};
```

Cuando existe un solo parámetro también pueden omitirse sus paréntesis:

```javascript
const duplicar = numero => numero * 2;
```

Con cero parámetros o con más de uno, los paréntesis son necesarios:

```javascript
const obtenerValor = () => 10;
const sumar = (a, b) => a + b;
```

La forma breve mejora la legibilidad cuando la operación es realmente simple; no constituye una obligación ni hace automáticamente mejor a una función.

---

# Callbacks

Un **callback** es una función que se pasa a otra función para que esta pueda utilizarla.

```javascript
function ejecutar(callback) {
  callback();
}

function informar() {
  console.log("Callback ejecutado");
}

ejecutar(informar);
```

En:

```javascript
function ejecutar(callback)
```

`callback` es un parámetro.

En:

```javascript
ejecutar(informar);
```

`informar` es el argumento y además cumple el rol de callback.

También es habitual:

```javascript
ejecutar(() => {
  console.log("Callback ejecutado");
});
```

Los callbacks aparecen en eventos, métodos de arrays, temporizadores y APIs asincrónicas.

Un callback **no es necesariamente asincrónico**: también puede ejecutarse inmediatamente de forma síncrona.

La función que recibe una función como argumento o devuelve otra función se denomina habitualmente **función de orden superior** (*higher-order function*). El callback es la función que se entrega para ser utilizada.

```javascript
function saludar(nombre) {
  return `Hola ${nombre}`;
}

function procesarNombre(nombre, callback) {
  return callback(nombre);
}

console.log(procesarNombre("Ana", saludar));
```

Aquí:

- `procesarNombre` es una función de orden superior porque recibe otra función;
- `saludar` cumple el rol de callback;
- `callback` es el parámetro que recibirá una función;
- `saludar` es el argumento concreto entregado en la llamada.

---

# Declaraciones de funciones y hoisting

Las **function declarations** pueden utilizarse antes de su posición textual en el archivo:

```javascript
saludar();

function saludar() {
  console.log("Hola");
}
```

Este comportamiento suele explicarse mediante el concepto de **hoisting**.

Hoisting es un modelo mental útil, pero no significa que el motor mueva físicamente líneas de código hacia arriba. Durante la preparación del contexto de ejecución, determinadas declaraciones quedan disponibles antes de que comience la ejecución de las instrucciones del cuerpo.

## Declaraciones repetidas con el mismo nombre

Declarar repetidamente funciones con el mismo nombre dentro del mismo ámbito es confuso y debe evitarse.

```javascript
function saludar() {
  return "Hola";
}

function saludar(nombre) {
  return `Hola ${nombre}`;
}
```

JavaScript no implementa la sobrecarga tradicional de funciones basada únicamente en distintas listas de parámetros como lenguajes como C# o Java. En este caso las declaraciones comparten el mismo nombre y la declaración efectiva posterior puede reemplazar la anterior dentro de ese ámbito.

Por eso no debe diseñarse una API JavaScript esperando que el motor elija automáticamente una implementación según la cantidad o tipo de argumentos.

---

# Asincronía

## Idea general

Una operación **asíncrona** permite iniciar trabajo cuyo resultado llegará más adelante sin bloquear necesariamente la continuación inmediata del flujo principal.

Ejemplos habituales en frontend:

- temporizadores;
- eventos del usuario;
- solicitudes HTTP;
- lectura de determinados recursos.

JavaScript ejecuta código sobre un modelo de ejecución coordinado con el entorno anfitrión. Las APIs del navegador o de Node.js pueden programar trabajo cuya continuación se ejecutará posteriormente.

La asincronía no significa que cada tarea se ejecute simplemente “en paralelo” dentro del mismo hilo de JavaScript. Para comprender su orden real será necesario estudiar posteriormente el **event loop**, las colas de tareas y las promesas.

## `setTimeout()`

`setTimeout()` solicita ejecutar una función después de que haya transcurrido **como mínimo** una demora indicada.

```javascript
setTimeout(() => {
  console.log("Pasaron al menos 3 segundos");
}, 3000);

console.log("Esto se ejecuta antes");
```

Salida esperable:

```text
Esto se ejecuta antes
Pasaron al menos 3 segundos
```

Los `3000` representan milisegundos.

La demora no garantiza un instante exacto. Significa que la función no debe ejecutarse antes de ese umbral; puede ejecutarse después si el entorno todavía está ocupado.

## Callback en `setTimeout()`

El primer argumento de `setTimeout()` es una función callback.

```javascript
function informar(nombre) {
  console.log(`Hola ${nombre}`);
}

setTimeout(informar, 3000, "Ana");
```

Aquí:

- `informar` es el callback;
- `3000` es la demora;
- `"Ana"` es un argumento que será entregado al callback cuando se ejecute.

También puede definirse el callback directamente:

```javascript
setTimeout(() => {
  console.log("Callback ejecutado");
}, 3000);
```

## Orden de ejecución

```javascript
console.log("A");

setTimeout(() => {
  console.log("B");
}, 1000);

console.log("C");
```

El resultado normal será:

```text
A
C
B
```

Registrar el temporizador no detiene la ejecución de las instrucciones siguientes.

Este modelo es fundamental para comprender posteriormente solicitudes HTTP, eventos, promesas y `async`/`await`.

---

# Scope léxico y modificación de bindings externos

Una función puede acceder a bindings definidos en un ámbito exterior:

```javascript
let contador = 0;

function incrementar() {
  contador += 1;
}

incrementar();

console.log(contador); // 1
```

La función no necesita retornar `contador` para que la reasignación sea observable afuera: está modificando el binding externo que se encuentra dentro de su alcance léxico.

Esto debe distinguirse del pasaje de argumentos.

```javascript
let numero = 10;

function incrementar(valor) {
  valor += 1;
}

incrementar(numero);

console.log(numero); // 10
```

Aquí el parámetro local `valor` recibe el valor primitivo `10`; modificar ese binding local no reasigna el binding exterior `numero`.

Por lo tanto, son mecanismos distintos:

- **capturar y modificar un binding externo** mediante scope léxico;
- **recibir un argumento en un parámetro local**.

---

# Asignación de primitivos y objetos

## Primitivos: copia del valor

```javascript
let a = 10;
let b = a;

a = 20;

console.log(a); // 20
console.log(b); // 10
```

El valor de `b` es independiente de la posterior reasignación de `a`.

## Objetos: referencia compartida

```javascript
const objeto1 = {
  nombre: "Carlos"
};

const objeto2 = objeto1;

objeto1.nombre = "Juan";

console.log(objeto2.nombre); // "Juan"
```

Ambos bindings permiten acceder al mismo objeto.

Un modelo mental útil:

```text
objeto1 ──┐
          ├──> { nombre: "Juan" }
objeto2 ──┘
```

Esto no significa que los objetos “no ocupen memoria”. Es una abstracción para comprender la semántica observable: al asignar un objeto a otra variable, se copia la referencia al mismo objeto, no se crea automáticamente un clon independiente.

## Comparación

```javascript
const a = { valor: 1 };
const b = { valor: 1 };

console.log(a === b); // false
```

Son dos objetos distintos.

```javascript
const a = { valor: 1 };
const b = a;

console.log(a === b); // true
```

Aquí ambos bindings refieren al mismo objeto.

---

# Gestión automática de memoria

JavaScript administra memoria automáticamente mediante mecanismos de **garbage collection**.

```javascript
let dato = {
  contenido: "temporal"
};

dato = null;
```

Si el objeto anterior deja de ser alcanzable desde el programa, el motor puede considerarlo candidato para recuperar su memoria.

El programa no controla el momento exacto en que ocurrirá la recolección.

---


# Integración de HTML, CSS y JavaScript

Una aplicación frontend suele separar responsabilidades entre distintos archivos:

```text
proyecto/
├── index.html
├── styles/
│   └── styles.css
└── scripts/
    └── script.js
```

La separación no es una restricción técnica absoluta, pero mejora la organización, reutilización y mantenimiento.

## Vincular CSS

Una hoja de estilos externa se vincula normalmente desde `<head>`:

```html
<link rel="stylesheet" href="./styles/styles.css">
```

## Vincular JavaScript

Un script externo clásico puede cargarse con:

```html
<script src="./scripts/script.js"></script>
```

Colocarlo cerca del final de `<body>` es una estrategia tradicional para ejecutar el script después de que el HTML principal ya haya sido analizado. También pueden utilizarse `defer` o módulos:

```html
<script defer src="./scripts/script.js"></script>
```

```html
<script type="module" src="./scripts/main.js"></script>
```

Los scripts de tipo módulo se procesan de forma diferida respecto del análisis del HTML.

---

# Manipulación práctica del DOM

## Seleccionar por `id`

```html
<p id="mensaje">Texto original</p>
```

```javascript
const mensaje = document.getElementById("mensaje");
```

El `id` debe identificar de forma única a un elemento dentro del documento.

## `innerText`

```javascript
mensaje.innerText = "Texto modificado";
```

Si se asigna una cadena que contiene etiquetas, se muestran como texto.

## `innerHTML`

```javascript
const contenedor = document.getElementById("contenedor");

contenedor.innerHTML = "<strong>Hola</strong>";
```

En este caso la cadena se interpreta como marcado HTML.

### Precaución

No debe insertarse con `innerHTML` contenido externo o proporcionado por usuarios sin tratamiento adecuado. Interpretar contenido no confiable como HTML puede introducir vulnerabilidades XSS.

---

# Eventos en la práctica

## Manejadores inline

```html
<button onclick="cambiarTexto()">Cambiar texto</button>
```

```javascript
function cambiarTexto() {
  const mensaje = document.getElementById("mensaje");
  mensaje.innerText = "Nuevo texto";
}
```

Esta forma permite visualizar el mecanismo evento → función, aunque mezcla comportamiento con marcado.

## `addEventListener()`

```html
<button id="btnCambiar">Cambiar texto</button>
```

```javascript
const boton = document.getElementById("btnCambiar");

boton.addEventListener("click", () => {
  console.log("Se hizo clic");
});
```

El tipo de evento es `"click"`, no `"onclick"`.

## Eventos usados en la clase

```text
click
keydown
change
```

Para reaccionar a cada modificación de texto de un `<input>`, el evento `input` suele resultar más específico que `keydown`.

---

# Formularios y valores

## Asociación entre `label` e `input`

```html
<label for="nombre">Nombre</label>
<input id="nombre" type="text">
```

El atributo `for` vincula la etiqueta con el control cuyo `id` coincide.

## Propiedad `value`

```html
<select id="color">
  <option value="red">Rojo</option>
  <option value="blue">Azul</option>
  <option value="green">Verde</option>
</select>
```

```javascript
const selector = document.getElementById("color");

console.log(selector.value);
```

Ese valor puede utilizarse en una estructura de control como `switch`.

---

# Modificación de estilos desde JavaScript

```javascript
const entrada = document.getElementById("entrada");

entrada.style.color = "red";
entrada.style.backgroundColor = "black";
entrada.style.fontWeight = "bold";
```

También existe `style.cssText`, pero para aplicaciones mantenibles suele ser preferible definir estilos en CSS y alternar clases desde JavaScript:

```javascript
entrada.classList.add("destacado");
```

---

# Construcción dinámica de contenido

```javascript
const compras = ["carne", "ensalada", "bebida", "postre"];

let items = "";

for (let i = 0; i < compras.length; i++) {
  items += `<li>${compras[i]}</li>`;
}

document.getElementById("lista").innerHTML = items;
```

Esta técnica ilustra cómo convertir datos en marcado. Más adelante también puede utilizarse la API DOM (`createElement`, `append`, etc.) para crear nodos directamente.

---

# Temporizadores aplicados a iteraciones

Programar varios `setTimeout()` dentro de un ciclo no hace que una iteración espere a la anterior.

Para escalonar acciones puede calcularse la demora con el índice:

```javascript
const elementos = ["A", "B", "C"];

elementos.forEach((elemento, indice) => {
  setTimeout(() => {
    console.log(elemento);
  }, indice * 1000);
});
```

Esto programa ejecuciones aproximadamente en 0 ms, 1000 ms y 2000 ms.

---

# Módulos de JavaScript

Los **ECMAScript Modules (ESM)** permiten dividir el programa en archivos con responsabilidades separadas y compartir explícitamente determinadas partes.

## Exportaciones nombradas

```javascript
export const html = {
  titulo: "HTML",
  descripcion: "Lenguaje de marcado"
};

export const css = {
  titulo: "CSS",
  descripcion: "Lenguaje de estilos"
};
```

También puede exportarse al final:

```javascript
const html = { titulo: "HTML" };
const css = { titulo: "CSS" };

export { html, css };
```

## Importaciones nombradas

```javascript
import { html, css } from "./lenguajes.js";
```

## Cargar un módulo desde HTML

```html
<script type="module" src="./scripts/main.js"></script>
```

Los módulos:

- poseen su propio ámbito;
- utilizan modo estricto automáticamente;
- admiten `import` y `export`;
- se ejecutan de forma diferida respecto del análisis HTML;
- no exponen automáticamente sus variables y funciones como globales.

Esto es relevante al combinar módulos con manejadores inline, porque una función interna del módulo no queda disponible automáticamente para `onclick="..."`.

---

# Selección con `querySelectorAll()`

`document.querySelectorAll()` recibe un selector CSS y devuelve una `NodeList` estática.

```javascript
const items = document.querySelectorAll("#lenguajes li");
```

Para seleccionar solo hijos directos:

```javascript
const items = document.querySelectorAll("#lenguajes > li");
```

Una `NodeList` no es un `Array`, aunque puede recorrerse con `forEach()`:

```javascript
items.forEach(item => {
  item.addEventListener("click", () => {
    console.log(item.innerText);
  });
});
```

Si se necesita convertirla:

```javascript
const arrayItems = Array.from(items);
```

---

# Ejercicio integrador de DOM y módulos

La clase combinó:

1. datos definidos como objetos en un módulo;
2. exportaciones e importaciones;
3. selección de varios elementos mediante `querySelectorAll()`;
4. recorrido con `forEach()`;
5. asociación prevista de eventos de clic;
6. actualización de título, subtítulo y descripción en el DOM.

El ejercicio quedó **sin funcionar al cierre de la clase** y fue dejado pendiente para la siguiente. No se incorpora una solución atribuida a la cursada hasta que aparezca en la clase posterior.

---

# Temas abiertos de JavaScript

Quedaron anunciados o todavía requieren mayor desarrollo:

- resolución del ejercicio integrador de módulos + DOM iniciado en la Clase 5;
- propagación y objeto `Event`;
- creación de nodos con la API DOM;
- event loop y modelo de ejecución asíncrona;
- promesas;
- consumo de APIs;
- TypeScript.

Estas secciones se ampliarán cuando la cursada las desarrolle.

---

# Panorama de la cursada técnica

La materia parte de los fundamentos de HTML y CSS para concentrarse posteriormente en JavaScript y Angular.

Dentro de Angular se anticiparon temas como:

- componentes;
- comunicación entre componentes;
- servicios;
- inyección de dependencias;
- enrutamiento;
- directivas;
- estructuras de control;
- pipes;
- formularios reactivos;
- formularios basados en plantillas;
- integración del frontend con un backend.

Estos conceptos se incorporarán a la biblioteca cuando sean desarrollados efectivamente por la cursada.

## Convención de Angular indicada por la cátedra

La cátedra indicó trabajar con **Angular 17 o superior** y priorizar la sintaxis moderna.

Angular 17 introdujo la nueva sintaxis de control de flujo incorporada en las plantillas, con construcciones como `@if` y `@for`.

Es importante distinguir este cambio de la arquitectura *standalone*: los componentes standalone existían antes de Angular 17 y los `NgModule` no desaparecieron en esa versión. Angular continúa soportando aplicaciones basadas en módulos, aunque el enfoque standalone es el estilo moderno y actualmente preferido para código nuevo.

Esta distinción permite conservar la decisión práctica de la materia —trabajar con Angular moderno— sin convertir una simplificación oral en una regla histórica incorrecta.

---

# Referencias técnicas

- MDN Web Docs — `<script>`: https://developer.mozilla.org/docs/Web/HTML/Reference/Elements/script
- MDN Web Docs — JavaScript modules: https://developer.mozilla.org/docs/Web/JavaScript/Guide/Modules
- MDN Web Docs — `getElementById()`: https://developer.mozilla.org/docs/Web/API/Document/getElementById
- MDN Web Docs — `querySelectorAll()`: https://developer.mozilla.org/docs/Web/API/Document/querySelectorAll
- MDN Web Docs — `NodeList`: https://developer.mozilla.org/docs/Web/API/NodeList
- MDN Web Docs — `innerText`: https://developer.mozilla.org/docs/Web/API/HTMLElement/innerText
- MDN Web Docs — `innerHTML`: https://developer.mozilla.org/docs/Web/API/Element/innerHTML
- MDN Web Docs — `classList`: https://developer.mozilla.org/docs/Web/API/Element/classList
- MDN Web Docs — `<label>`: https://developer.mozilla.org/docs/Web/HTML/Reference/Elements/label

- MDN Web Docs — DOM: https://developer.mozilla.org/docs/Web/API/Document_Object_Model
- MDN Web Docs — Events: https://developer.mozilla.org/docs/Learn_web_development/Core/Scripting/Events
- MDN Web Docs — `addEventListener()`: https://developer.mozilla.org/docs/Web/API/EventTarget/addEventListener
- MDN Web Docs — `try...catch`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch
- MDN Web Docs — Array: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array
- MDN Web Docs — `filter()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
- MDN Web Docs — `find()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/find
- MDN Web Docs — `findIndex()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex
- MDN Web Docs — `some()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/some
- MDN Web Docs — `every()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/every
- MDN Web Docs — `slice()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/slice
- MDN Web Docs — `splice()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/splice
- MDN Web Docs — `forEach()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach
- MDN Web Docs — `map()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/map
- MDN Web Docs — `sort()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/sort
- MDN Web Docs — `toSorted()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/toSorted

- MDN Web Docs — Template literals: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals
- MDN Web Docs — JSON: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON
- MDN Web Docs — `JSON.stringify()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify
- MDN Web Docs — `JSON.parse()`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse
- MDN Web Docs — Functions: https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions
- MDN Web Docs — Hoisting: https://developer.mozilla.org/docs/Glossary/Hoisting
- MDN Web Docs — `setTimeout()`: https://developer.mozilla.org/docs/Web/API/Window/setTimeout

- MDN Web Docs — JavaScript Guide: https://developer.mozilla.org/docs/Web/JavaScript/Guide
- MDN Web Docs — JavaScript execution model: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Execution_model
- MDN Web Docs — Grammar and types: https://developer.mozilla.org/docs/Web/JavaScript/Guide/Grammar_and_types
- MDN Web Docs — `let`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/let
- MDN Web Docs — `const`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/const
- MDN Web Docs — `var`: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/var
- MDN Web Docs — Arrow functions: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Functions/Arrow_functions
- MDN Web Docs — Data structures: https://developer.mozilla.org/docs/Web/JavaScript/Data_structures
- MDN Web Docs — Memory management: https://developer.mozilla.org/docs/Web/JavaScript/Guide/Memory_management

- MDN Web Docs — HTML: https://developer.mozilla.org/docs/Web/HTML
- MDN Web Docs — HTML semántico y accesibilidad: https://developer.mozilla.org/docs/Learn_web_development/Core/Accessibility/HTML
- Angular — documentación oficial: https://angular.dev/
- Angular — migración a control flow: https://angular.dev/reference/migrations/control-flow
- Angular — migración a standalone: https://angular.dev/reference/migrations/standalone
