Preguntas para React
¿Qué es React?
React es una biblioteca de JavaScript de código abierto para construir interfaces de usuario. Está basada en la componetización de la UI: la interfaz se divide en componentes independientes, que contienen su propio estado. Cuando el estado de un componente cambia, React vuelve a renderizar la interfaz.

Esto hace que React sea una herramienta muy útil para construir interfaces complejas, ya que permite dividir la interfaz en piezas más pequeñas y reutilizables.

Fue creada en 2011 por Jordan Walke, un ingeniero de software que trabajaba en Facebook y que quería simplificar la forma de crear interfaces de usuario complejas.

Es una biblioteca muy popular y es usada por muchas empresas como Facebook, Netflix, Airbnb, Twitter, Instagram, etc.

⬆ Volver a índice

¿Cuáles son las características principales de React?
Las características principales de React son:

Componentes: React está basado en la componetización de la UI. La interfaz se divide en componentes independientes, que contienen su propio estado. Cuando el estado de un componente cambia, React vuelve a renderizar la interfaz.

Virtual DOM: React usa un DOM virtual para renderizar los componentes. El DOM virtual es una representación en memoria del DOM real. Cuando el estado de un componente cambia, React vuelve a renderizar la interfaz. En lugar de modificar el DOM real, React modifica el DOM virtual y, a continuación, compara el DOM virtual con el DOM real. De esta forma, React sabe qué cambios se deben aplicar al DOM real.

Declarativo: React es declarativo, lo que significa que no se especifica cómo se debe realizar una tarea, sino qué se debe realizar. Esto hace que el código sea más fácil de entender y de mantener.

Unidireccional: React es unidireccional, lo que significa que los datos fluyen en una sola dirección. Los datos fluyen de los componentes padres a los componentes hijos.

Universal: React se puede ejecutar tanto en el cliente como en el servidor. Además, puedes usar React Native para crear aplicaciones nativas para Android e iOS.

⬆ Volver a índice

¿Qué significa exactamente que sea declarativo?
No le decimos cómo debe renderizar la interfaz a base de instrucciones. Le decimos qué debe renderizar y React se encarga de renderizarlo.

Un ejemplo entre declarativo e imperativo:

// Declarativo
const element = <h1>Hello, world</h1>

// Imperativo
const element = document.createElement('h1')
element.innerHTML = 'Hello, world'
⬆ Volver a índice

¿Qué es un componente?
Un componente es una pieza de código que renderiza una parte de la interfaz. Los componentes pueden ser parametrizados, reutilizados y pueden contener su propio estado.

En React los componentes se crean usando funciones o clases.

⬆ Volver a índice

¿Qué es JSX?
React usa JSX para declarar qué debe renderizar. JSX es una extensión de JavaScript que permite escribir un código más cercano visualmente a HTML, que mejora la legibilidad del código y hace que sea más fácil de entender.

Sin JSX, deberíamos usar React.createElement para crear los elementos de la interfaz manualmente de esta forma:

import { createElement } from 'react'

function Hello () { // un componente es una función! 👀
  return React.createElement(
    'h1', // elemento a renderizar
     null, // atributos del elemento
    'Hola Mundo 👋🌍!' // contenido del elemento
  )
}
Esto es muy tedioso y poco legible. Por eso, React usa JSX para declarar qué debe renderizar. Por eso usamos JSX de esta forma:

function Hello () {
  return <h1>Hola Mundo 👋🌍!</h1>
}
Ambos códigos son equivalentes.

⬆ Volver a índice

¿Cómo se transforma el JSX?
El JSX se transforma en código JavaScript compatible en el navegador usando un transpilador o compilador. El más famoso es a día de hoy Babel, que utiliza una serie de plugins para ser compatible con la transformación, pero existen otros como SWC.

Puedes ver cómo se transforma el JSX en el playground de código de Babel.

Hay casos especiales en los que un transpilador no es necesario. Por ejemplo, Deno tiene soporte nativo para la sintaxis JSX y no es necesario transformar el código para hacerlo compatible.

⬆ Volver a índice

¿Cuál es la diferencia entre componente y elemento en React?
Un componente es una función o clase que recibe props y devuelve un elemento. Un elemento es un objeto que representa un nodo del DOM o una instancia de un componente de React.

// Elemento que representa un nodo del DOM
{
  type: 'button',
  props: {
    className: 'button button-blue',
    children: {
      type: 'b',
      props: {
        children: 'OK!'
      }
    }
  }
}

// Elemento que representa una instancia de un componente
{
  type: Button,
  props: {
    color: 'blue',
    children: 'OK!'
  }
}
⬆ Volver a índice

¿Cómo crear un componente en React?
Los componentes en React son funciones o clases que devuelven un elemento de React. Hoy en día lo más recomendado es usar funciones:

function HelloWorld() {
  return <h1>Hello World!</h1>
}
Pero también puedes usar una clase para crear un componente React:

import { Component } from 'react'

class HelloWorld extends Component {
  render() {
    return <h1>Hello World!</h1>
  }
}
Lo importante es que el nombre de la función o clase empiece con una letra mayúscula. Esto es necesario para que React pueda distinguir entre componentes y elementos HTML.

⬆ Volver a índice

¿Qué son las props en React?
Las props son las propiedades de un componente. Son datos que se pasan de un componente a otro. Por ejemplo, si tienes un componente Button que muestra un botón, puedes pasarle una prop text para que el botón muestre ese texto:

function Button(props) {
  return <button>{props.text}</button>
}
Podríamos entender que el componente Button es un botón genérico, y que la prop text es el texto que se muestra en el botón. Así estamos creando un componente reutilizable.

Debe considerarse además que al usar cualquier expresión JavaScript dentro de JSX debe envolverlos con {}, en este caso el objeto props, de otra forma JSX lo considerará como texto plano.

Para usarlo, indicamos el nombre del componente y le pasamos las props que queremos:

<Button text="Haz clic aquí" />
<Button text="Seguir a @midudev" />
Las props son una forma de parametrizar nuestros componentes igual que hacemos con las funciones. Podemos pasarle cualquier tipo de dato a un componente, incluso otros componentes.

⬆ Volver a índice

¿Qué es y para qué sirve la prop children en React?
La prop children es una prop especial que se pasa a los componentes. Es un objeto que contiene los elementos que envuelve un componente.

Por ejemplo, si tenemos un componente Card que muestra una tarjeta con un título y un contenido, podemos usar la prop children para mostrar el contenido:

function Card(props) {
  return (
    <div className="card">
      <h2>{props.title}</h2>
      <div>{props.children}</div>
    </div>
  )
}
Y luego podemos usarlo de la siguiente forma:

<Card title="Título de la tarjeta">
  <p>Contenido de la tarjeta</p>
</Card>
En este caso, la prop children contiene el elemento <p>Contenido de la tarjeta</p>.

Conocer y saber usar la prop children es muy importante para crear componentes reutilizables en React.

⬆ Volver a índice

 ¿Qué diferencia hay entre props y state?
Las props son un objeto que se pasan como argumentos de un componente padre a un componente hijo. Son inmutables y no se pueden modificar desde el componente hijo.

El state es un valor que se define dentro de un componente. Su valor es inmutable (no se puede modificar directamente) pero se puede establecer un valor nuevo del estado para que React vuelva a renderizar el componente.

Así que mientras que tanto props como state afectan al renderizado del componente, su gestión es diferente.

⬆ Volver a índice

¿Qué es el renderizado condicional en React?
El renderizado condicional es la forma de mostrar un componente u otro dependiendo de una condición.

Para hacer renderizado condicional en React usamos el operador ternario:

function Button({ text }) {
  return text
    ? <button>{text}</button>
    : null
}
En este caso, si la prop text existe, se renderiza el botón. Si no existe, no se renderiza nada.

Es común encontrar implementaciones del renderizado condicional con el operador &&, del tipo:

function List({ listArray }) {
  return listArray?.length && listArray.map(item=>item)
}
Parece que tiene sentido... si el length es positivo (mayor a cero) pintamos el map. !Pues no! ❌ Cuidado, si tiene length de cero ya que se pintará en el navegador un 0.

Es preferible utilizar el operador ternario. Kent C. Dodds tiene un artículo interesante hablando del tema. Use ternaries rather than && in JSX

⬆ Volver a índice

¿Cómo puedes aplicar clases CSS a un componente en React y por qué no se puede usar class?
Para aplicar clases CSS a un componente en React usamos la prop className:

function Button({ text }) {
  return (
    <button className="button">
      {text}
    </button>
  )
}
La razón por la que se llama className es porque class es una palabra reservada en JavaScript. Por eso, en JSX, tenemos que usar className para aplicar clases CSS.

⬆ Volver a índice

¿Cómo puedes aplicar estilos en línea a un componente en React?
Para aplicar estilos CSS en línea a un componente en React usamos la prop style. La diferencia de cómo lo haríamos con HTML, es que en React los estilos se pasan como un objeto y no como una cadena de texto (esto puede verse más claro con los dobles corchetes, los primeros para indicar que es una expresión JavaScript, y los segundos para crear el objeto):

function Button({ text }) {
  return (
    <button style={{ color: 'red', borderRadius: '2px' }}>
      {text}
    </button>
  )
}
Fíjate que, además, los nombres de las propiedades CSS están en camelCase.

⬆ Volver a índice

¿Cómo puedo aplicar estilos de forma condicional a un componente en React?
Puedes aplicar estilos de forma condicional a un componente en React usando la prop style y un operador ternario:

function Button({ text, primary }) {
  return (
    <button style={{ color: primary ? 'red' : 'blue' }}>
      {text}
    </button>
  )
}
En el caso anterior, si la prop primary es true, el botón tendrá el color rojo. Si no, tendrá el color azul.

También puedes seguir la misma mecánica usando clases. En este caso, usamos el operador ternario para decidir si añadir o no la clase:

function Button({ text, primary }) {
  return (
    <button className={primary ? 'button-primary' : ''}>
      {text}
    </button>
  )
}
También podemos usar bibliotecas como classnames:

import classnames from 'classnames'

function Button({ text, primary }) {
  return (
    <button className={classnames('button', { primary })}>
      {text}
    </button>
  )
}
En este caso, si la prop primary es true, se añadirá la clase primary al botón. Si no, no se añadirá. En cambio la clase button siempre se añadirá.

⬆ Volver a índice

¿Qué es el renderizado de listas en React?
El renderizado de listas es la forma de iterar un array de elementos y renderizar elementos de React para cada uno de ellos.

Para hacer renderizado de listas en React usamos el método map de los arrays:

function List({ items }) {
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  )
}
En este caso, se renderiza una lista de elementos usando el componente List. El componente List recibe una prop items que es un array de objetos del tipo [{id:1, name: "John", id:1, name: "Doe"}]. El componente List renderiza un elemento li por cada elemento del array.

El elemento li tiene una prop key que es un identificador único para cada elemento. Esto es necesario para que React pueda identificar cada elemento de la lista y actualizarlo de forma eficiente. Más adelante hay una explicación más detallada sobre esto.

⬆ Volver a índice

¿Cómo añadir un evento a un componente en React?
Para añadir un evento a un componente en React usamos la sintaxis on y el nombre del evento nativo del navegador en camelCase:

function Button({ text, onClick }) {
  return (
    <button onClick={onClick}>
      {text}
    </button>
  )
}
En este caso, el componente Button recibe una prop onClick que es una función. Cuando el usuario hace clic en el botón, se ejecuta la función onClick.

⬆ Volver a índice

¿Cómo puedo pasar un parámetro a una función que maneja un evento en React?
Para pasar un parámetro a una función que maneja un evento en React podemos usar una función anónima:

function Button({ id, text, onClick }) {
  return (
    <button onClick={() => onClick(id)}>
      {text}
    </button>
  )
}
Cuando el usuario hace clic en el botón, se ejecuta la función onClick pasándole como parámetro el valor de la prop id.

También puedes crear una función que ejecuta la función onClick pasándole el valor de la prop id:

function Button({ id, text, onClick }) {
  const handleClick = (event) => { // handleClick recibe el evento original
    onClick(id)
  }

  return (
    <button onClick={handleClick}>
      {text}
    </button>
  )
}
⬆ Volver a índice

¿Qué es el estado en React?
El estado es un objeto que contiene datos que pueden cambiar en el tiempo. En React, el estado se usa para controlar los cambios en la interfaz.

Para que entiendas el concepto, piensa en el interruptor de una habitación. Estos interruptores suelen tener dos estados: encendido y apagado. Cuando accionamos el interruptor y lo ponemos en on entonces la luz se enciende y cuando lo ponemos en off la luz se apaga.

Este mismo concepto se puede aplicar a la interfaz de usuario. Por ejemplo, el botón Me Gusta de Facebook tendría el estado de meGusta a true cuando el usuario le ha dado a Me Gusta y a false cuando no lo ha hecho.

No solo podemos tener en el estado valores booleanos, también podemos tener objetos, arrays, números, etc.

Por ejemplo, si tienes un componente Counter que muestra un contador, puedes usar el estado para controlar el valor del contador.

Para crear un estado en React usamos el hook useState:

import { useState } from 'react'

function Counter() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count + 1)}>Aumentar</button>
    </div>
  )
}
Al usar el hook useState este devolverá un array de dos posiciones:

El valor del estado.
La función para cambiar el estado.
Suele usarse desestructuración para facilitar la lectura y ahorrarnos algunas lineas de código. Por otro lado, al pasarle un dato como parámetro al useState le estamos indicando su estado inicial.

Con un componente de clase, la creación del estado sería así:

import { Component } from 'react'

class Counter extends Component {
  constructor(props) {
    super(props)
    this.state = { count: 0 }
  }

  render() {
    return (
      <div>
        <p>Contador: {this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Aumentar
        </button>
      </div>
    )
  }
}
⬆ Volver a índice

¿Qué son los hooks?
Los Hooks son una API de React que nos permite tener estado, y otras características de React, en los componentes creados con una function.

Esto, antes, no era posible y nos obligaba a crear un componente con class para poder acceder a todas las posibilidades de la librería.

Hooks es gancho y, precisamente, lo que hacen, es que te permiten enganchar tus componentes funcionales a todas las características que ofrece React.

⬆ Volver a índice

¿Qué hace el hook useState?
El hook useState es utilizado para crear variables de estado, quiere decir que su valor es dinámico, que este puede cambiar en el tiempo y eso requiere una re-renderización del componente donde se utiliza

Recibe un parámetro:

El valor inicial de nuestra variable de estado.
Devuelve un array con dos variables:

En primer lugar tenemos la variable que contiene el valor
La siguiente variable es una función set, requiere el nuevo valor del estado, y este modifica el valor de la variable que anteriormente mencionamos
Cabe destacar que la función proporciona cómo parámetro el valor actual del propio estado. Ex: setIsOpen(isOpen => !isOpen)
En este ejemplo mostramos como el valor de count se inicializa en 0, y también se renderiza cada vez que el valor es modificado con la función setCount en el evento onClick del button:

import { useState } from 'react'

function Counter() {
  const [count, setCount] = useState(0)

  return (
    <>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count => count + 1)}>Aumentar</button>
    </>
  )
}
⬆ Volver a índice

¿Qué significa la expresión "subir el estado"?
Cuando varios componentes necesitan compartir los mismos datos de un estado, entonces se recomienda elevar ese estado compartido hasta su ancestro común más cercano.

Dicho de otra forma. Si dos componentes hijos comparten los mismos datos de su padre, entonces mueve el estado al padre en lugar de mantener un estado local en sus hijos.

Para entenderlo, lo mejor es que lo veamos con un ejemplo. Imagina que tenemos una lista de regalos deseados y queremos poder añadir regalos y mostrar el total de regalos que hay en la lista.

import { useState } from 'react'

export default function App () {
  return (
    <>
      <h1>Lista de regalos</h1>
      <GiftList />
      <TotalGifts />
    </>
  )
}

function GiftList () {
  const [gifts, setGifts] = useState([])

  const addGift = () => {
    const newGift = prompt('¿Qué regalo quieres añadir?')
    setGifts([...gifts, newGift])
  }

  return (
    <>
      <h2>Regalos</h2>
      <ul>
        {gifts.map(gift => (
          <li key={gift}>{gift}</li>
        ))}
      </ul>
      <button onClick={addGift}>Añadir regalo</button>
    </>
  )
}

function TotalGifts () {
  const [totalGifts, setTotalGifts] = useState(0)

  return (
    <>
      <h2>Total de regalos</h2>
      <p>{totalGifts}</p>
    </>
  )
}
¿Qué pasa si queremos que el total de regalos se actualice cada vez que añadimos un regalo? Como podemos ver, no es posible porque el estado de totalGifts está en el componente TotalGifts y no en el componente GiftList. Y como no podemos acceder al estado de GiftList desde TotalGifts, no podemos actualizar el estado de totalGifts cuando añadimos un regalo.

Tenemos que subir el estado de gifts al componente padre App y le pasaremos el número de regalos como prop al componente TotalGifts.

import { useState } from 'react'

export default function App () {
  const [gifts, setGifts] = useState([])

  const addGift = () => {
    const newGift = prompt('¿Qué regalo quieres añadir?')
    setGifts([...gifts, newGift])
  }

  return (
    <>
      <h1>Lista de regalos</h1>
      <GiftList gifts={gifts} addGift={addGift} />
      <TotalGifts totalGifts={gifts.length} />
    </>
  )
}

function GiftList ({ gifts, addGift }) {
  return (
    <>
      <h2>Regalos</h2>
      <ul>
        {gifts.map(gift => (
          <li key={gift}>{gift}</li>
        ))}
      </ul>
      <button onClick={addGift}>Añadir regalo</button>
    </>
  )
}

function TotalGifts ({ totalGifts }) {
  return (
    <>
      <h2>Total de regalos</h2>
      <p>{totalGifts}</p>
    </>
  )
}
Con esto, lo que hemos hecho es elevar el estado. Lo hemos movido desde el componente GiftList al componente App. Ahora pasamos como prop los regalos al componente GiftList y una forma de actualizar el estado, y también hemos pasado como prop al componente TotalGifts el número de regalos.

Código de ejemplo
⬆ Volver a índice

¿Qué hace el hook useEffect?
El hook useEffect se usa para ejecutar código cuando se renderiza el componente o cuando cambian las dependencias del efecto.

Recibe dos parámetros:

La función que se ejecutará al cambiar las dependencias o al renderizar el componente.
Un array de dependencias. Si cambia el valor de alguna dependencia, ejecutará la función.
En este ejemplo mostramos un mensaje en consola cuando carga el componente y cada vez que cambia el valor de count:

import { useEffect, useState } from 'react'

function Counter() {
  const [count, setCount] = useState(0)

  useEffect(() => {
    console.log('El contador se ha actualizado')
  }, [count])

  return (
    <>
      <p>Contador: {count}</p>
      <button onClick={() => setCount(count + 1)}>Aumentar</button>
    </>
  )
}
⬆ Volver a índice

Explica casos de uso del hook useEffect
Podemos usar el hook useEffect de diferentes formas, tales como:

Ejecutar código cuando se renderiza el componente, cuando cambian las dependencias del efecto o cuando se desmonta el componente.
Por eso puede ser útil para hacer llamadas a APIs, ya que sea nada más montar el componente o cuando cambian las dependencias.
Realizar tracking de eventos, como Google Analytics, para saber qué páginas visitan los usuarios.
Podemos validar un formulario para que cada vez que cambie el estado, podamos actualizar la UI y mostrar dónde están los errores.
Podemos suscribirnos a eventos del navegador, como por ejemplo el evento resize para saber cuando el usuario cambia el tamaño de la ventana.
⬆ Volver a índice

¿Cómo podemos ejecutar código cuando el componente se monta?
Podemos ejecutar código cuando el componente se monta usando el hook useEffect sin pasarle ninguna dependencia. En este caso, la función que se pasa como primer parámetro se ejecutará cuando el componente se monte.

import { useEffect } from 'react'

function Component() {
  useEffect(() => {
    console.log('El componente se ha montado')
  }, [])

  return (
    <p>Abre la consola y re-dimensiona la ventana</p>
  )
}
⬆ Volver a índice

¿Qué son los Fragments en React?
Los Fragments son una forma de agrupar elementos sin añadir un elemento extra al DOM, ya que React no permite devolver varios elementos en un componente, solo un elemento raíz.

Para crear un Fragment en React usamos el componente Fragment:

import { Fragment } from 'react'

function App() {
  return (
    <Fragment>
      <h1>Titulo</h1>
      <p>Párrafo</p>
    </Fragment>
  )
}
También podemos usar la sintaxis de abreviatura:

function App() {
  return (
    <>
      <h1>Titulo</h1>
      <p>Párrafo</p>
    </>
  )
}
⬆ Volver a índice

¿Qué es el Compound Components Pattern?
Es un patrón de diseño de componentes que se basa en crear un componente padre con un solo objetivo, proporcionarle a sus hijos las propiedades necesarias para que se rendericen sin problemas.

Permite una estructura declarativa a la hora de construir nuevos componentes, además ayuda a la lectura del código por su simplicidad y limpieza.

Un ejemplo de este diseño sería una lista que renderiza los elementos hijos:

<List>
  <ListItem>Cat</ListItem>
  <ListItem>Dog</ListItem>
</List>
const List = ({ children, ...props }) => (
  <ul {...props} >
    {children}
  </ul>
);

const ListItem = ({ children, ...props }) => {

  return (
    <li {...props}>
      {children}
    </li>
  );
};

export { List, ListItem };
Este es un ejemplo sencillo, pero los componentes pueden ser tan complejos como quieras y tanto el padre como los hijos pueden tener sus propios estados.

Enlaces de interés:

Lleva tu React al siguiente nivel con Compound Pattern by dezkareid en el blog de Platzi

Compound Components by Jenna Smith en inglés

Compound Components Lesson by Kent C. Dodds en inglés

⬆ Volver a índice

¿Cómo puedes inicializar un proyecto de React desde cero?
Existen diversas formas de inicializar un proyecto de React desde cero. Entre las más populares están:

Vite
npm create vite@latest my-app -- --template react
Create React App
npx create-react-app my-app
La opción más popular y recomendada hoy en día es Vite. Fuente npm trends.

Usando un Framework, entre las más populares están:

Nextjs
npx create-next-app@latest my-app
Gatsby
npm init gatsby
La opción más popular y recomendada hoy en día es Nextjs. Fuente npm trends

Cada uno de ellos es un empaquetador de aplicaciones web. Se encargan de resolver las dependencias de tu proyecto, levantar un entorno de desarrollo que se refresca automáticamente con cada cambio y de empaquetar tu aplicación para producción con todos los archivos estáticos necesarios y mucho más.

⬆ Volver a índice

¿Qué es React DOM?
React DOM es la librería que se encarga de renderizar los componentes de React para el navegador. Hay que tener en cuenta que React es una biblioteca que se puede usar en diferentes entornos (dispositivos móviles, apps de escritorio, terminal...).

Mientras que la biblioteca de React, a secas, es el motor de creación de componentes, hooks, sistema de props y estado... React DOM es la librería que se encarga de renderizar los componentes de React específicamente en el navegador.

React Native, por ejemplo, haría lo mismo, pero para dispositivos móviles.

⬆ Volver a índice

¿Qué JavaScript necesito para aprender React?
JavaScript que necesitas para aprender React
Para aprender y dominar React necesitas saber JavaScript. A diferencia de otros frameworks y bibliotecas, como Angular y Vue, que se basan en su propio DSL (Domain-Specific Language), React usa una extensión de la sintaxis de JavaScript llamada JSX. Más adelante lo veremos en detalle pero, al final, no deja de ser azúcar sintáctico para escribir menos JavaScript.

En React todo es JavaScript. Para bien y para mal. Este libro da por sentados unos conocimientos previos del lenguaje de programación pero antes de empezar vamos a hacer un pequeño repaso por algunas de las características más importantes que necesitarás conocer.

Si ya dominas JavaScript puedes saltarte este capítulo y continuar con el libro, pero recuerda que siempre podrás revisar este capítulo como referencia.

EcmaScript Modules o ESModules
Los EcmaScript Modules es la forma nativa que tiene JavaScript para importar y exportar variables, funciones y clases entre diferentes ficheros. Hoy en día, especialmente si trabajamos con un empaquetador de aplicaciones como Webpack, vamos a estar trabajando constantemente con esta sintaxis.

Por un lado podemos crear módulos exportándolos por defecto:

// sayHi.js
// exportamos por defecto el módulo sayHi
export default sayHi (message) {
    console.log(message)
}

// index.js
// este módulo lo podremos importar con el nombre que queramos
import sayHi from './sayHi.js'

// al ser el módulo exportado por defecto podríamos usar otro nombre
import miduHi from './sayHi.js'
También podemos hacer exportaciones nombradas de módulos, de forma que un módulo tiene un nombre asignado y para importarlo necesitamos usar exactamente el nombre usado al exportarlo:

// sayHi.js
// podemos usar exportaciones nombradas para mejorar esto
export const sayHi = (message) => console.log(message)

// y se pueden hacer tantas exportaciones de módulos nombrados como queramos
export const anotherHi = msg => alert(msg)

// index.js
// ahora para importar estos módulos en otro archivo podríamos hacerlo así
import {sayHi, anotherHi} from './sayHi.js'
Los imports que hemos visto hasta aquí se conocen como imports estáticos. Esto significa que ese módulo será cargado en el momento de la carga del archivo que lo importa.

También existen los imports dinámicos, de forma que podamos importar módulos que se carguen en el momento de la ejecución del programa o cuando nosotros decidamos (por ejemplo, como respuesta a un click).

document.querySelector('button').addEventListener('click', () => {
  // los imports dinámicos devuelven una Promesa
  import('./sayHi.js').then(module => {
    // ahora podemos ejecutar el módulo que hemos cargado
    module.default('Hola')
  })
})
A> Los imports dinámicos son útiles también cuando trabajamos con empaquetadores como Webpack o Vite, ya que esto creará unos chunks (fragmentos) que se cargarán fuera del bundle general. ¿El objetivo? Mejorar el rendimiento de la aplicación.

Existen más sintaxis para trabajar con módulos, pero con saber las que hemos visto ya sería suficiente para seguir el libro.

¿Por qué es importante

Para empezar React te ofrece diferentes partes de su biblioteca a través de módulos que podrás importar. Además nuestros componentes los tendremos separados en ficheros y, cada uno de ellos, se podrá importar utilizando ESModules.

Además, por temas de optimización de rendimiento, podremos importar de forma dinámica componentes y así mejorar la experiencia de nuestros usuarios al necesitar cargar menos información para poder utilizar la página.

Operador condicional (ternario)
Las ternarias son una forma de realizar condiciones sin la necesidad de usar la sintaxis con if. Se podría decir que es una forma de atajo para evitar escribir tanto código.

if (number % 2 === 0) {
  console.log('Es par')
} else {
  console.log('Es impar')
}

// usando ternaria
number % 2 === 0 ? console.log('Es par') : console.log('Es impar')
¿Por qué es importante

En las interfaces gráficas es muy normal que, dependiendo del estado de la aplicación o los datos que nos lleguen, vamos a querer renderizar una cosa u otra en pantalla. Para realizar esto, en lugar de utilizar if se usan las ternarias ya que queda mucho más legible dentro del JSX.

Funciones flecha o Arrow Functions
Las funciones flecha o arrow function fueron añadidas a JavaScript en el estándar ECMAScript 6 (o ES2015). En principio parece que simplemente se trata de una sintaxis alternativa más simple a la hora de crear expresiones de funciones:

const nombreDeLaFuncion = function (param1, param2) {
  // instrucciones de la función
}

const nombreDeLaFuncion = (param1, param2) => { // con arrow function
  // instrucciones de la función
}
Pero además del cambio de sintaxis existen otras características de las funciones flechas que se usan constantemente en React.

// return implícito al escribir una sola línea
const getName = () => 'midudev'

// ahorro de parentésis para función de un parámetro
const duplicateNumber = num => num * 2

// se usan mucho como callback en funciones de arrays
const numbers = [2, 4, 6]
const newNumbers = numbers.map(n => n / 2)
console.log(newNumbers) // [1, 2, 3]
También tiene algunos cambios respecto al valor de this pero, aunque es aconsejable dominarlo, no es realmente necesario para poder seguir con garantías el libro.

¿Por qué es importante

Aunque hace unos años con React se trabajaba principalmente con clases, desde la irrupción de los hooks en la versión 16.8 ya no se usan mucho. Esto hace que se usen mucho más funciones.

Las funciones flecha, además, puedes verlas fácilmente conviviendo dentro de tus componentes. Por ejemplo, a la hora de renderizar una lista de elementos ejecutarás el método .map del array y, como callback, seguramente usarás una función flecha anónima.

Parámetros predeterminados (default values)
En JavaScript puedes proporcionar valores por defecto a los parámetros de una función en caso que no se le pase ningún argumento.

// al parámetro b le damos un valor por defecto de 1
function multiply(a, b = 1) {
  return a * b;
}

// si le pasamos un argumento con valor, se ignora el valor por defecto
console.log(multiply(5, 2)) // 10

// si no le pasamos un argumento, se usa el valor por defecto
console.log(multiply(5)) // 5

// las funciones flecha también pueden usarlos
const sayHi = (msg = 'Hola React!') => console.log(msg)
sayHi() // 'Hola React!'
¿Por qué es importante

En React existen dos conceptos muy importantes: componentes y hooks. No vamos a entrar en detalle ahora en ellos pero lo importante es que ambos son construidos con funciones.

Poder añadir valores por defecto a los parámetros de esas funciones en el caso que no venga ningún argumento es clave para poder controlar React con éxito.

Los componentes, por ejemplo, pueden no recibir parámetros y, pese a ello, seguramente vas a querer que tengan algún comportamiento por defecto. Lo podrás conseguir de esta forma.

Template Literals
Los template literals o plantillas de cadenas llevan las cadenas de texto al siguiente nivel permitiendo expresiones incrustadas en ellas.

const inicio = 'Hola'
const final = 'React'

// usando una concatenación normal sería
const mensaje = inicio + " " + final

// con los template literals podemos evaluar expresiones
const mensaje = `${inicio} ${final}`
Como ves, para poder usar los template literals, necesitas usar el símbolo ```

Además, también nos permiten utilizar cadenas de texto de más de una línea.

¿Por qué es importante

En React esto se puede utilizar para diferentes cosas. No sólo es normal crear cadenas de texto para mostrar en la interfaz... también puede ser útil para crear clases para tus elementos HTML de forma dinámica. Verás que los template literales están en todas partes.

Propiedades abreviadas
Desde ECMAScript 2015 se puede iniciar un objeto utilizado nombre de propiedades abreviadas. Esto es que si quieres utilizar como valor una variable que tiene el mismo nombre que la key, entonces puedes indicar la inicialización una vez:

const name = 'Miguel'
const age = 36
const book = 'React'

// antes haríamos esto
const persona = { name: name, age: age, book: book }

// ahora podemos hacer esto, sin repetir
const persona = { name, age, book }
¿Por qué es importante

En React se trata muchas veces con objetos y siempre vamos a querer escribir el menor número de líneas posible para mantener nuestro código fácil de mantener y entender.

La desestructuración
La sintaxis de desestructuración es una expresión de JavaScript que permite extraer valores de Arrays o propiedades de objetos en distintas variables.

// antes
const array = [1, 2, 3]
const primerNumero = array[0]
const segundoNumero = array[1]

// ahora
const [primerNumero, segundoNumero] = array

// antes con objetos
const persona = { name: 'Miguel', age: 36, book: 'React' }
const name = persona.name
const age = persona.age

// ahora con objetos
const {age, name} = persona

// también podemos añadir valores por defecto
const {books = 2} = persona
console.log(persona.books) // -> 2

// también funciona en funciones
const getName = ({name}) => `El nombre es ${name}`
getName(persona)
¿Por qué es importante

En React hay mucho código básico que da por sentado que conoces y dominas esta sintaxis. Piensa que los objetos y los arreglos son tipos de datos que son perfectos para guardar datos a representar en una interfaz. Así que poder tratarlos fácilmente te va a hacer la vida mucho más fácil.

Métodos de Array
Saber manipular arreglos en JavaScript es básico para considerar que se domina. Cada método realiza una operación en concreto y devuelve diferentes tipos de datos. Todos los métodos que veremos reciben un callback (función) que se ejecutará para cada uno de los elementos del array.

Vamos a revisar algunos de los métodos más usados:

// tenemos este array con diferentes elementos
const networks = [
  {
    id: 'youtube',
    url: 'https://midu.tube',
    needsUpdate: true
  },
  {
    id: 'twitter',
    url: 'https://twitter.com/midudev',
    needsUpdate: true
  },
  {
    id: 'instagram',
    url: 'https://instagram.com/midu.dev',
    needsUpdate: false
  }
]

// con .map podemos transformar cada elemento
// y devolver un nuevo array
networks.map(singleNetwork => singleNetwork.url)
// Resultado:
  [
    'https://midu.tube',
    'https://twitter.com/midudev',
    'https://instagram.com/midu.dev'
  ]

// con .filter podemos filtrar elementos de un array que no
// pasen una condición determinada por la función que se le pasa.
// Devuelve un nuevo array.
networks.filter(singleNetwork => singleNetwork.needsUpdate === true)
// Resultado:
[
  { id: 'youtube', url: 'https://midu.tube', needsUpdate: true },
  { id: 'twitter', url: 'https://twitter.com/midudev', needsUpdate: true }
]

// con .find podemos buscar un elemento de un array que
// cumpla la condición definida en el callback
networks.find(singleNetwork => singleNetwork.id === 'youtube')
// Resultado:
{ id: 'youtube', url: 'https://midu.tube', needsUpdate: true }

// con .some podemos revisar si algún elemento del array cumple una condición
networks.some(singleNetwork => singleNetwork.id === 'tiktok') // false
networks.some(singleNetwork => singleNetwork.id === 'instagram') // true
¿Por qué es importante

En React es muy normal almacenar los datos que tenemos que representar en la UI como array. Esto hace que muchas veces necesitemos tratarlos, filtrarlos o extraer información de ellos. Es primordial entender, conocer y dominar al menos estos métodos, ya que son los más usados.

Sintaxis Spread
La sintaxis de spread nos permite expandir un iterable o un objeto en otro lugar dónde se espere esa información. Para poder utilizarlo, necesitamos utilizar los tres puntos suspensivos ... justo antes.

const networks = ['Twitter', 'Twitch', 'Instagram']
const newNetwork = 'Tik Tok'
// creamos un nuevo array expandiendo el array networks y
// colocando al final el elemento newNetwork
// utilizando la sintaxis de spread
const allNetworks = [...networks, newNetwork]
console.log(allNetworks)
// -> [ 'Twitter', 'Twitch', 'Instagram', 'Tik Tok' ]
Esto mismo lo podemos conseguir con un objeto, de forma que podemos expander todas sus propiedades en otro objeto de forma muy sencilla.

const midu = { name: 'Miguel', twitter: '@midudev' }
const miduWithNewInfo = {
  ...midu,
  youtube: 'https://youtube.com/midudev',
  books: ['Aprende React']
}
console.log(miduWithNewInfo)
// {
//   name: 'Miguel',
//   twitter: '@midudev',
//   youtube: 'https://youtube.com/midudev',
//   books: [ 'Aprende React' ]
// }
Es importante notar que esto hace una copia, sí, pero superficial. Si tuviéramos objetos anidados dentro del objeto entonces deberíamos tener en cuenta que podríamos mutar la referencia. Veamos un ejemplo.

const midu = {
  name: 'Miguel',
  twitter: '@midudev',
  experience: {
    years: 18,
    focus: 'javascript'
  }
}

const miduWithNewInfo = {
  ...midu,
  youtube: 'https://youtube.com/midudev',
  books: ['Aprende React']
}

// cambiamos un par de propiedades de la "copia" del objeto
miduWithNewInfo.name = 'Miguel Ángel'
miduWithNewInfo.experience.years = 19

// hacemos un console.log del objeto inicial
console.log(midu)

// en la consola veremos que el nombre no se ha modificado
// en el objeto original pero los años de experiencia sí
// ya que hemos mutado la referencia original
// {
//   name: 'Miguel',
//   twitter: '@midudev',
//   experience: { years: 19, focus: 'javascript' }
// }
¿Por qué es importante

En React es muy normal tener que añadir nuevos elementos a un array o crear nuevos objetos sin necesidad de mutarlos. El operador Rest nos puede ayudar a conseguir esto. Si no conoces bien el concepto de valor y referencia en JavaScript, sería conveniente que lo repases.

Operador Rest
La sintaxis ... hace tiempo que funciona en JavaScript en los parámetros de una función. A esta técnica se le llamaba parámetros rest y nos permitía tener un número indefinido de argumentos en una función y poder acceder a ellos después como un array.

function suma(...allArguments) {
  return allArguments.reduce((previous, current) => {
    return previous + current
  })
}
Ahora el operador rest también se puede utilizar para agrupar el resto de propiedades un objeto o iterable. Esto puede ser útil para extraer un elemento en concreto del objeto o el iterable y crear una copia superficial del resto en una nueva variable.

const midu = {
  name: 'Miguel',
  twitter: '@midudev',
  experience: {
    years: 18,
    focus: 'javascript'
  }
}

const {name, ...restOfMidu} = midu

console.log(restOfMidu)
// -> {
//   twitter: '@midudev',
//   experience: {
//     years: 18,
//     focus: 'javascript'
//   }
// }
También podría funcionar con arrays:

const [firstNumber, ...restOfNumbers] = [1, 2, 3]
console.log(firstNumber) // -> 1
console.log(restOfNumbers) // -> [2, 3]
¿Por qué es importante

Es una forma interesante de eliminar (de forma figurada) una propiedad de un objeto y creando una copia superficial del resto de propiedades. A veces puede ser interesante para extraer la información que queremos de unos parámetros y dejar el resto en un objeto que pasaremos hacia otro nivel.

Encadenamiento opcional (Optional Chaining)
El operador de encadenamiento opcional ?. te permite leer con seguridad el valor de una propiedad que está anidada dentro de diferentes niveles de un objeto.

De esta forma, en lugar de revisar si las propiedades existen para poder acceder a ellas, lo que hacemos es usar el encadenamiento opcional.

const author = {
  name: 'Miguel',
  libro: {
    name: 'Aprendiendo React'
  },
  writeBook() {
    return 'Writing!'
  }
};

// sin optional chaining
(author === null || author === undefined)
    ? undefined
    : (author.libro === null || author.libro === undefined)
    ? undefined
    : author.libro.name 

// con optional chaining
author?.libro?.name
¿Por qué es importante

Un objeto es una estructura de datos que es perfecta a la hora de representar muchos elementos de la UI. ¿Tienes un artículo? Toda la información de un artículo seguramente la tendrás representada en un objeto.

Conforme tu UI sea más grande y compleja, estos objetos tendrán más información y necesitarás dominar el encadenamiento opcional ?. para poder acceder a su información con garantías.

¿Qué son los High Order Components (HOC)?
Los High Order Components son funciones que reciben un componente como parámetro y devuelven un componente.

function withLayout(Component) {
  return function(props) {
    return <main>
      <section>
        <Component {...props} />
      </section>
    </main>
  }
}
En este caso, la función withLayout recibe un componente como parámetro y devuelve un componente. El componente devuelto renderiza el componente que se le pasa como parámetro dentro de un layout.

Es un patrón que nos permite reutilizar código y así podemos inyectar funcionalidad, estilos o cualquier otra cosa a un componente de forma sencilla.

Con la llegada de los hooks, los HOCs se han vuelto menos populares, pero todavía se usan en algunos casos.

⬆ Volver a índice

¿Qué son las render props?
Son un patrón de diseño de React que nos permite reutilizar código entre componentes e inyectar información en el renderizado de los componentes.

<DataProvider render={data => (
  <h1>Hello {data.target}</h1>
)}/>
En este caso, el componente DataProvider recibe una función render como prop. Ahí le indicamos qué es lo que debe renderizar usando la información que recibe como parámetro.

La implementación del DataProvider con funciones podría ser la siguiente:

function DataProvider({ render }) {
  const data = { target: 'world' }
  return render(data)
}
También se puede encontrar este patrón usando la prop children en los componentes.

<DataProvider>
  {data => (
    <h1>Hello {data.target}</h1>
  )}
</DataProvider>
Y la implementación sería similar:

function DataProvider({ children }) {
  const data = { target: 'world' }
  return children(data)
}
Este patrón es usado por grandes bibliotecas como react-router, formik o react-motion.

⬆ Volver a índice

¿Por qué no podemos usar un if en el renderizado de un componente?
En React, no podemos usar un if en el renderizado de un componente porque no es una expresión válida de JavaScript, es una declaración. Las expresiones son aquellas que devuelven un valor y las declaraciones no devuelven ningún valor.

En JSX solo podemos usar expresiones, por eso usamos ternarias, que sí son expresiones.

// ❌ Esto no funciona
function Button({ text }) {
  return (
    <button>
      {if (text) { return text } else { return 'Click' }}
    </button>
  )
}
// ✅ Esto funciona
function Button({ text }) {
  return (
    <button>
      {text ? text : 'Click'}
    </button>
  )
}
De la misma forma, tampoco podemos usar for, while o switch dentro del renderizado de un componente.

⬆ Volver a índice

¿Qué es el StrictMode en React?
El StrictMode es un componente que nos permite activar algunas comprobaciones de desarrollo en React. Por ejemplo, detecta componentes que se renderizan de forma innecesaria o funcionalidades obsoletas que se están usando.

import { StrictMode } from 'react'

function App() {
  return (
    <StrictMode>
      <Component />
    </StrictMode>
  )
}
⬆ Volver a índice

¿Para que sirve el useReduce y que problemas resuelve
Bien, esto no será una respuesta como tal, ya que, depende del tipo de proyecto, pero, se pueden tomar como recomendaciones para tomar una decisión:

Cuando el estado siguiente del "state" depende del estado anterior. Cuando manejas un objeto JSON como state y tienes subvalores dentro de tu mismo objeto. Cuando la lógica es muy compleja. El Hook useContext permite comunicar componentes funcionales a través del contexto en React. El Hook useContext debe recibir el contexto total como argumento.

const [state, dispatch] = useReducer(reducer, initialArg, init);
⬆ Volver a índice

¿Para que sirve el useContext y que problemas resuelve?
Al useContext lo podemos definir como un Hook que permite comunicar componentes funcionales a través del contexto en React.

Entonces, este Hook recibe un objeto de contexto y retorna el valor del contexto actual, el cual si recordamos un poco, el valor del contexto actual lo asignamos a través de value en el provider:

<MyContext.Provider value={value}>
⬆ Volver a índice
