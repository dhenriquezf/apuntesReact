# Apuntes React

## Parte 1 Creando App y Tipos de componentes
Lo primero que debemos hacer es instalar nodeJS en nuestro equipo
verificamos su version de npm y npx:

```
npm -v
npx -v
```
Creando proyecto por defecto de React
Para crear un proyecto de react estandar pre configurado usamos el comando create-react-app, sitio web usando la plantilla por defecto:

```
npx create-react-app nombre-de-tu-proyecto
```

Con npx podemos probar react sin necesidad de instalar las librerias en nuestro equipo, para ejecutar comandos o paquetes sin tener que instalarlos de manera global

La creacion del proyecto puede tardar in poco, una vez ya listo ingresamos a la carpeta (por terminal) e iniciamos el servidor de desarrollo:

```
npm start
```

Esto se instala en una carpeta todo el proyecto funciona con esto sin esto no arranca

<!-- NOTA
buscar que era npx (para ejecutar comandos o paquetes sin tener que instalarlos de manera global) -->

Al ejecutar npm start la terminal muestra la ip y se despliega el sitio web basico de react

**Conceptos basicos del proyecto**
- node_modules -> *son las (elementos) librerias que usa react, nunca se sube a producción*
- public -> *archivos publicos, para subir a producción (archivo favicon.icon, manifest.json) aqui se encuentra nuestro archivo index.html principal, aqui esta el dom*
- src -> *aqui esta toda la aplicación (serviceWorker.js => escucha los cambios en nuestra aplicación), los archivos de js, css, sass, jsx*
- .gitignore -> *archivo que contiene todo los elementos o carpetas que no seran subidos al repositorio*
- package.json -> *contiene toda la informacion  y configuracion de nuestro proyecto*
- README.md -> *archivo que contiene una descripción del proyecto, en este caso tiene un manual (tambien lo puede tener)*

***NOTA: averiguar que es o como funciona el serviceWorker.js***

## Agregar nuevos componentes (elementos) al proyecto pre generado de react

Debemos crear una carpeta llamada componentes donde estaran todos los componentes que conformaran el proyecto.

**Componente Stateful**

Dentro de la carpeta Components crearemos un archivo llamado Stateful.js (la extension puede cambiar a jsx) donde importar las librerias de react y components, creamos la clase con el nombre Stateful que extendera de Components (puede importar aqui directamente la libreria componentes) y posteriormente crearemos un constructor para la clase Statefull y tambien un metodo llamado render, este ultimo se encarga de retornar el HTML que crearemos, luego se debe exportar el nuevo componente (la clase especificamente).

Stateful -> *Los componentes de tipo Stateful se encarga manejar los ciclos de vida, eventos y los estados de los elementos (componentes) este tipo de componentes se crean como una clase, son los unicos que se crean como clase.*

**Pasos:**
1. Crear carpeta Components en src
2. Crear archivo Stateful.js
3. Importar React y Components
4. Crear clase Stateful que extiende de Components
5. Crear metodo Contructor para la clase
6. Crear metodo render para la clase
7. Exportar clase (componente)

```
import React from 'react';
import Component from 'react';

class Stateful extends Component {
  constructor(){
    super();
    this.state = {
      hello: 'Hello World'
    }
  }

  render(){
    return (
      <p>{this.state.hello}</p>
    )
  }
}

export default Stateful;
```

<!-- primer componente a crear sera un Stateful.js (Capitalcase) NOTA: descripcion mas abajo

import dentro del archivos Libreria de react

Stateful debe extender de Components (libreria de react)

crear constructor en la clase Stateful y funcion render() (retorna la funcion la pagina)

exportar la clase. -->
**Componente Stateless**

Dentro de la carpeta Components crearemos un archivo llamado Stateless.js (la extension puede cambiar a jsx) donde importar las librerias de react, creamos una funcion de tipo flecha con el nombre Stateless posteriormente crearemos un metodo llamado render, este ultimo se encarga de retornar el HTML que crearemos luego se debe exportar el nuevo componente (la funcion especificamente).

Stateless -> *Los componentes de tipo Stateful no depende de tener un estado o un ciclo de vida solo presenta logica, son funciones, solo lo que necesitamos se agrega aqui.*

**Pasos:**
1. Crear carpeta Components en src
2. Crear archivo Stateless.js
3. Importar React
4. Crear funcion flecha Stateful
5. Crear metodo render para la funcion
7. Exportar funcion (componente)

```
import React from 'react';

const Stateless = () => {
  return (
    <p className="Stateless">This is another hello world from a stateless component</p>
  )
}

export default Stateless;
```
<!-- crear un Stateless.js

import react library

create constants Stateless as a function and return html into -> ()

export function -->

**Componente Presentacional**

Dentro de la carpeta Components crearemos un archivo llamado Presentacional.js (la extension puede cambiar a jsx) donde importar las librerias de react, creamos una funcion de tipo flecha con el nombre Presentacional posteriormente crearemos un metodo llamado render, este ultimo se encarga de retornar el HTML que crearemos luego se debe exportar el nuevo componente (la funcion especificamente).

Presentacional -> *Los componentes de tipo Presentacional no tienen logica ni propiedades se encargan de mostrar el html, de como se vera los elementos, tienen una parte particular de html usa funciones pero no logica.(averiguar mas).*

**Pasos:**
1. Crear carpeta Components en src
2. Crear archivo Presentacional.js
3. Importar React
4. Crear funcion flecha Presentacional
5. Crear metodo render para la funcion
7. Exportar funcion (componente)

```
import React from 'react';

const Presentational = () => <p>This is a message from a presentational component</p>

export default Presentational;
```

***NOTA: se recomiendo que los nombre de los archivos sean con Capitalcase***
<!-- crear un Presentacional.js

importar react

crear constante como funcion y retorna html entre parentesis (usar arrow function)

exporta constante -->


<!-- Stateful -> se encarga manejar los ciclos de vida eventos y los estados de los elementos,es una clase -->

<!-- Stateless -> no depende de tener un estado o un ciclo de vida solo presenta logica, son funciones, solo lo que necesitamos. -->

<!-- Presentacionales -> no tienen logica ni propiedades se encargan de mostrar el html, de como se vera los elementos, tienen una parte particular de html usa funciones pero no logica.(averiguar mas) -->

## Parte 2 - JSX JavaScript + HTML:

JSX -> *sintaxis que usa react para mezclar javascripts, html y css en un solo componente (componente = archivo) esto nos permite tener todo el codigo perteneciente a un componente en un solo archivo.*

Para usarlo se crea un archivo en componentes (crear carperta componentes en src) con extension jsx, un componente presentacional para este caso (igual se puede usar la extension js), la diferencia hoy en dia solo causa que el IDE te entregue o no ayuda respecto a codigo react (si usas jsx) mas que eso no afecta a tu codigo ya que el transpilador (BABEL en este caso) logra entender ambas extensiones sin problemas.

Es importante tener en cuenta que en los componentes de react no podemos usar la palabra clave class para asignarle una clase a los elementos de HTML esta palabra se debe reemplazar por className de lo contrario obtendremos un error, esto se puede modificar para que se pueda utilizar de todos modos pero por defecto no se permite.

Para agregar contenido de js como el valor de una variable a los elementos de HTML se usan las llaves {}, Es importante cerrar todas las etiquetas de HTML de lo contrario se generaran errores al compilar el codigo. Asi como podemos agregar variables de JS al HTML tambien podemos agregar codigo de JS como condicionales (un if ternario por ejemplo) al igual que la variable se usan llaves para incrustar el JS en el HTML.

***NOTA: Es una buena practica crear primero el esqueleto del componente y luego rellenar con el resto del codigo, import clase o funcion y export***

```
<div className="HelloWorld">
    <h1>{Hello}</h1>
    <h2>Curso Escencial de React</h2>
    <img src="https://arepa.s3.amazonaws.com/react.png" alt="React"/>
    {isTrue ? <h4>Esto es verdadero</h4> : <h5>Soy falso</h5>}
    {isTrue && <h6>Soy verdadero</h6>}
</div>
```
Para visualizar este componente asi como en los anteriores ejemplos debemos de conectarlo con el archivo index.js que es el encargado de mostrar y desplegar el contenido en el browser. Esto lo hacemos mediante el import de este componente en el index.js.

En el archivo de index.js tenemos lo que es react, reactDOM, CSS y otro componentes, basicamente importamos aqui todo lo que sea necesario para el proyecto incluyendo el nuevo componentes.

una vez importado el componente debemos agregar este al metodo render de la clase ReactDOM, este metodo recibe dos parametros, el o los componentes y el elemento donde se mostrara (elemento HTML), aqui obtendremos el elemento con su id mediante JS.

```
ReactDOM.render(<HolaMundo /> ---> este es el componente, document.getElementById('root'));
```

**Pasos**
1. Crear componente presentacional (Stateless) en Components
2. Importar react
3. Crear función constante
4. Exportar componente
5. Agregar return a la funcion
6. Agregar codigo HTML al return de la función
7. Agregamos el codigo JS que necesitemos, variables, validaciones como un IF, etc...
8. Importamos en index.js (puede variar el nombre... supongo)
9. Pasamos por parametro el componente a la función render del ReactDOM y elemento HTML donde se mostrara
10. Correr proyecto

***NOTA: Cuando importamos no es necesario especificar la extensión del archivo***
<!-- para los elementos de la clase los HTML debe reemplazar el class por className -->

<!-- para añadir el contenido (como el valor de una variable) del elemento de html se usan -> {} en el elemento html -->

<!-- se deben cerrar todas las etiquetas (HTML) -->
<!-- podemos hacer validaciones (como un if ternario) dentro del return de la funcion, en el html -->

<!-- para visualizar el componente creado en el sitio se debe conectar a la aplicacion en el archivos index.js, donde se encuentra la configuracion del proyecto, aqui tenemos react y reactDOM, archivo de css, y otros componentes.
Aqui debemos importar el componente que se creo nuevo. -->

<!-- no es necesario al importar especificar la extension de los archivos. -->

<!-- para mostrar el componente importado se debe agregar en los parentesis de la funcion render del ReactDOM.
Ejemplo:
-->

<!-- ## Crear un elemento .jsx del tipo presentacional
importamos react
creamos una constante (funcion)
exportamos el componente

la funcion creada sera la encargada de retornar el codigo html que se mostrara en pantalla
dentro del return (entre parentesis) creamos el codigo html
(un stateless es similar a un presentacional ? averiguar)

podemos agregar variables y mostrarlas en el html entre llaves
e incluso podemos agregar validaciones entre llaves (como un if ternario)

una vez creado se importa en el index.js y lo agregamos al render de reactDOM
con esto deberia poder verse este componente en el index -->

## Parte 3 Prop - Comunicacion entre componentes:

Asi como podemos pasar parametros a los componentes tambien podemos pasar propiedades a nuestros componentes independientes del tipo de componentes que este sea, sin embargo si necesitas manipular dichas propiedades es necesario instanciarlas en una nueva variable en nuestro componente.

El envio de las propiedades se realizara en el archivo de index.js al momento de entregar el componentes como parametro al metodo render, junto con el componente enviaremos la propiedad.

```
ReactDOM.render(
  <Button text="¡Hola!" />,  document.getElementByid('root'),
);
```

Crearemos un nuevo componente llamada Button para este ejemplo, realizaremos los pasos base para crear un componentes de tipo funcion (Stateless) y en el return de nuestro componentes crearemos un boton en un div al cual le enviaremos un texto que sera enviado por medio de las propiedades.

```
import React from 'react';

const Button = props => {
    return(
        <div>
            <button type="button">{props.text}</button>

        </div>
    )
};

export default Button;
```

Se puede ver que el componente (la función) obtiene como parametro de entrada la o las propiedades que luego podemos usar, en este caso se le extrajo de props la variable text (debe tener el mismo nombre que asignamos en el index.js) de este modo al cargar nuestro proyecto se vera un boton con el texto que nosotros enviemos. 

Existe otra forma para poder usar las propiedades dentro de nuestro componente, desestructurar los datos, extraer el valor de text de las props esta forma es un poco mas amigable:

```
const { text } = props
```

Y ya con esto podemos asignarsela directamente al elemento boton y de igual formar podemos enviar mas de una propiedad al componentes separando por comas las propiedades en el index.js e usar las dos formas:

```
const props = {
  text1: "Click1",
  text2: "Click2"}

ReactDOM.render(
    <Button {text1: "Click1", text2: "Click2"} />,
  document.getElementById('root')
);
```
```
import React from 'react';

//este es un componente stateless porque no maneja estados
const ButtonStateless = props => {
    //desestructuracion del elemento
    const { text1, text2 } = props
    return(
        <div>
            <button type="button">{props.text1}</button>
            <button type="button">{props.text2}</button>
            <button type="button">{text1}</button>
            <button type="button">{text2}</button>
        </div>
    )
};

export default ButtonStateless;
```

De mismo modo podemos mejorar un poco mas el codigo del index.js y crear objeto que contenga las variables y enviar el objeto como parametro a nuestro componente:

```
const props = {
  text1: "Click1",
  text2: "Click2"}

ReactDOM.render(
    <Button {...props} />,
  document.getElementById('root')
);
```


## Parte 4 Metodos de ciclo de vida:

Metodos del ciclo de vida (similares a los de android):

**Fases de los componentes de react:**
- Montaje => Constructor, render, ComponentDidMount
- Actualizacion => getDerivedStateFromProps, shouldComponentUpdate, render, componentDidUpdate
- Desmontaje => componentWillUnmont
- Manejo de Errores => getDerivedStateFromError, componentDidCatch

Los componentes de React pasan por fases estas fases se las llama Ciclo de vida del componente, aplica a todos los componentes, en algunos casos no se pueden ver como codigo mientras que en otros se pueden llamar dentro de nuestro componente para asignar alguna actividad segun queramos.

Los componentes pasa por 4 pasos:
***(revisar para posible mejora de explicacion***

#### Montaje:
En esta fase nuestro componente se crea junto a la lógica y los componentes internos y luego es insertado en el DOM.

**Constructor()**

Este es el primer método al que se hace un llamado, aquí es donde se inicializan los métodos controladores, eventos del estado.

**getDerivedStateFromProps()**

Este método se llama antes de presentarse en el DOM y nos permite actualizar el estado interno en respuesta a un cambio en las propiedades, es considerado un método de cuidado, ya que su implementación puede causar errores sutiles.

**render()**

Si queremos representar elementos en el DOM en este método es donde se escribe esta lógica, usualmente utilizamos JSX para trabajar y presentar nuestra aplicación.

**ComponentDidMount()**

Este método se llama inmediatamente que ha sido montado en el DOM, aquí es donde trabajamos con eventos que permitan interactuar con nuestro componente.

#### Actualización:
En esta fase nuestro componente está al pendiente de cambios que pueden venir a través de un cambio en “state” o “props” esto en consecuencia realizan una acción dentro de un componente.

**getDerivedStateFromProps()**

Este método es el primero en ejecutarse en la fase de actualización y funciona de la misma forma que en el montaje.

**shouldComponentUpdate()**

Dentro de este método se puede controlar la fase de actualización, podemos devolver un valor entre verdadero o falso si queremos actualizar o no el componente y es utilizado principalmente para optimización.

**render()**

Se llama el método render que representa los cambios en el DOM.

**componentDidUpdate()**

Este método es invocado inmediatamente después de que el componente se actualiza y recibe como argumentos las propiedades y el estado y es donde podemos manejar nuestro componente.

#### Desmontaje:
En esta etapa nuestro componente “Muere” cuando nosotros no necesitamos un elemento de nuestra aplicación, podemos pasar por este ciclo de vida y de esta forma eliminar el componente de la representación que tiene en el DOM.

**componentWillUnmount()**

Este método se llama justo antes de que el componente sea destruido o eliminado del DOM.

#### Manejo de Errores:
Cuando nuestro código se ejecuta y tiene un error, podemos entrar en una fase donde se puede entender mejor qué está sucediendo con la aplicación.

Algo que debemos tener en cuenta es que un componente NO debe pasar por toda las fases, un componente puede ser montado y desmontado sin pasar por la fase de actualización o manejo de errores.

Ahora que entendemos las fases que cumple el ciclo de vida en React vamos a entrar a detalle en cada uno de ellos para ver qué piezas de código se ejecutan y nos ayudarán a crear aplicaciones en React pasando por un ciclo de vida bien estructurado.

**getDerivedStateFromError()**

Una vez que se lanza un error este es el primer método que se llama, el cual recibe el error como argumento y cualquier valor devuelto en este método es utilizado para actualizar el estado del componente.

**componentDidCatch()**

Este método es llamado después de lanzarse un error y pasa como argumento el error y la información representada sobre el error.

Ahora que entendemos cada una de las fases que tiene el ciclo de vida de react, podemos utilizarlas según sea necesario en nuestra aplicación y de esta forma crear las interacciones que necesitemos.

## Parte 5:

Crear componente Stateful con estados y eventos:
una vez teniendo creado el proyecto creamos un componente de tipo stateful, de tipo clase, este extendera de Componente, esta puede traerse desde el import o directamente al extender (React.Component), Clase base:
```
class NombreClase extends Component {  }
```
Al crear la clase le agregamos el metodo render a la clase (metod de montaje), con su correspondiente return:
```
class NombreClase extends Component {
  render() { return() }
}
```

para terminar exportamos la clase (componente):

```
export default NombreClase.
```
Ahora podemos agregar un objeto en la clase que tendra el estado, en este caso un contados:

```
state = { count: 0,} (debe ir antes del render)
```

ahora en nuetro return vamos a agregar nuestro html que sera visualizado, crearemos un mensaje con el contador y un boton que ira aumentando el contador (el estado supuestamente), para poder mostrar la varible del estado debemos guardala en una variable dentro del metodo render, usamos destructuracion:
```
render() {
  const { count } = this.state
  return (
    <div>
      <p>Manzanas: {count}</p>
      <button type="button">Click</button>
    </div>
  )
}
```
con esto podemos mostrar la variable del objeto estado, deberia poder correr el proyecto y visualizar mas no aumentar el contador. Ahora creamos una funcion que ira incrementando el contador dentro de la clase, usaremos el metodo setState para setear el valor de count del objeto estado:
```
handleClick = () => {
  this.SetState({
    count: this.state.count + 1
  })
}
```
Ahora Agregamos el evento onClick al boton llamando a la funcion creada 'handleClick', el llamado a la funcion debe ser mediante llaves {}:
```
<button onClick={this.handleClick} type="button">Click</button>
```
Con esto el contador podra incrementar.



los componentes Stateful son clases que extienden de React.Components, puedes extender desde el import o desde la misma clase (React.Component)
dentro de la clase usas la funcion render y esta funcion retorna el html.

El estado en react es un objeto que le puedes definir variables de todo tipo y al que podemos acceder desde nuestro componente desde el momento en que se inicializa.
Ejemplo:
(detro de la clase) 
```
state = {
  count: 0,
}
```
este objeto lo podemos desestructurar dentro de la funcion render de la clase para usarlo en el html (al parecer la variable que almacenara el dato debe ir dentro del metodo render, averiguar):
Ejemplo:
```
const { count } = this.state (siguiendo el ejemplo de arriba)
```
Eventos (html):
Deben usar camelCase

creamos una funcion para el ejemplo:
```
handleClick = () => ( this.setState({ count: this.state.count + 1 }));
```
esta funcion se la debemos asignar al evento onClick del elemento HTML:
```
onClick{this.handleClick}
```
## Parte 6 - INSTALACION Y CONFIGURACION DE ENTORNO:
REACT
WEBPACK
BABEL
ESLING

git init

npm init -y => inicializar el proyecto, con la Y se preconfigura y se crea automaticamente, esto crea el package.json

Crear estandar de trabajo basico:
src => todo el codigo
public => elementos y archivos para produccion
components => va dentro de src
index.html => este archivo va dentro de public
index.js => este archivo va dentro de src (entrada del proyecto)

instalar react
npm install --save react react-dom

OJO CON LAS VULNERABILIDADES AL INSTALAR.

al instalar react se crea el archivos package-lock.json, permite manejar el versionado de los paquetes que instales
en el archivo package.json se agregan las dependencias de react y ReactDOM.

## Parte 7 - INSTALACION Y CONFIGURACION DE ENTORNO (BABEL):

NOTA: No solo configuramos aqui tambien creamos un componente base llamado HelloWorld.
Creamos el componente HelloWorld (o el que quieras), en components, importamos React y creamos el componente con una constante (funcion flecha) que retornara un simple hola mundo en html, y luego lo exportamos:

```
import React from 'react'

const HelloWorld = () => {
  <h1>Hello World</h1>
}

export default HelloWorld;
```

Ahora debemos crear (si no lo esta aun) nuestro archivo de entrada, que basicamente es el primer archivo que sera detectado en nuestro proyecto, el index.js, aqui se trabaja con toda la configuracion de react (almenos en este proyecto, no se si es siempre haci):
creamos archivo index.js en la raiz de la carpeta src (si es que no se creo en el paso anterior)
aqui importamos react y ReactDOM, reactDOM trabaja junto con react, esta se encarga de 'empujar' todo lo que hacemos con react hacia el navegador.

Aqui no creamos un nuevo componente si no que utilizamos reactDom para pasar los componentes creados.
utilizamos ReactDOM para pasar el componente por medio del metodo render:
```
ReactDOM.render()
```
tenemos que importar el componente en el index.js y se lo pasamos como parametro al metodo render. Los componentes (hasta ahora, no se si es todo asi) se pasan como parametro con la siguiente estructura: -> <NombreComponente />

render recibe dos elementos, el componente y donde voy a empujar el componente (la parte el html)
```
ReactDOM.render(< HelloWorld />, document.getElementById('id del elemento donde se visualizara el componente entregado a render'))
```

en el archivo de public le daremos vida a todo
creamos nuestra base de HTML (head, html, body, title...)
creamos un div le asignamos un id y ese id se envia al render de ReactDOM

Instalacion de BABEL
Con babel podemos crear y convertir JavaScripts moderno en JavaScripts compatible con todos los navegadores.

install babel:
```
npm install --save-dev @babel/core @babel/preset-env @babel/preset-react babel-loader
```
con el comando --save-dev indicamos que estas librerias se usaran en el ambiente (dependencia) de desarrollo.
--save-dev => indica que es solo para desarrollo la dependencia

Averiguar que hacen estas librerias.
@babel/core
babel-loader
@babel/preset-env
@babel/preset-react


se debe crea el archivo .babelrc para la configuracion de BABEL, en la raiz del proyecto

aqui agregamos las configuracion de todo lo instalado de babel, se crea un objeto en el archivo de babel para agregar las configuraciones, un objeto vacio -> {} sin asignarlo a variables (como se hiso en el objeto que guarda el estado en el componente de tipo stateful).

@babel/core -> todas las herramientas para convertir a codigo moderno
@babel/preset-env -> para trabajar con ECMScript 5 y 6
@babel/preset-react -> para trabajar con REACT (no estoy seguro si es asi o al reves con el de arriba)
babel-loader -> trabaja con webpack

creamos un objeto y le agregamos un arreglo llamado presents que contenga el nombre de los preset que se instalaron => @babel/preset-env @babel/preset-react 
uno ayuda a trabajar con ESMASCRIPT y el otro con jsx y react
Ejemplo:
```
{
  "presents": [
    "@babel/preset-env"
    "@babel/preset-react"
    ]
}
```
## Parte 8 - INSTALACION Y CONFIGURACION DE ENTORNO (webpack):

webpack se encarga de preparar el proyecto para desarrollo o pasar proyeccion, se encarga de los archivos dejarlos listos para todo
npm install webpack webpack-cli html-webpack-plugin html-loader  --save-dev

configurar archivo maestro de webpack
este se crea en la raiz llamado webpack.config.js -> aqui va toda la configuracion

lo primero es agregar path desde path:

const path = require('path')

luego instanciamos el plugin que instalamos -> html-webpack-plugin
const HtmlWebPackPlugin = requiere('html-webpack-plugin')

luego vamos a crear un modulo que exportaremos con la configuracion
aqui configuraremos todo lo que necesitamos

creamos el module llamamos a export
primero ponemos la entrada, que en este caso sera el archivo principal -> index.js (NOTA: revisar si puedon o necesito poner mas entradas dependiendo del proyecto)
luego agregamos nuestras salidas, donde guardaremos los archivos resultantes cuando compilemos, con path indicamos donde se guiardara, con resolve obtendremos el directorio donde nos encontramos
y ademas le pasamos el nombre de la carpeta donde guardaremos todo, y con filename le damos un nombre al archivo principal.

ahora añadimos resolve para resolver las extensiones que tenemos en el proyecto en este caso .js y .jsx, esto es en una lista de extensiones.
ahora creamos un modulo con las reglas necesario para nuestro proyecto, dentro creamos rules, la regla principal sera identificar las extensiones de nuestros archivos
esto se hace mediante expresiones regulares, luego agregamos la exclusion de node_modules o de lo que necesitemos excluir
luego agregamos el loader que usaremos con use, aqui agregamos un loader.

luego creamos nueva regla que nos permitira trabajar con los elementos HTML aqui agregamos el tipo de archivos y el loader a usar
luego agregamos los plugins que necesitamos, creamos dentro de plugins creamos una referencia a HtmlWebPackPlugin y le pasamos como parametro un objeto con la configuracion que necesitamos
los primernos elementos que necesitamos es el template (donde esta ubicado) y el nombre de archivo que tendra

revisar el archivo que este todo y bien escrito.

nos vamos a package.json para crear el script que compilara el proyecto
creamos uno llamado build y le pasamos la configuracion necesaria -> webpack --mode production

con esto vamos a la terminal y ejecutamos npm run build
esto nos mostrada un hash para identificar el compilado version tiempo archivos y si ocurrio algun problema
si revisamos nuestro proyecto encontraremos los archivos que le indicamos a webpack que creara dentro de dist
```
module.exports={
    entry: './src/index.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    },
    resolve:{
        extensions: ['.js', '.jsx']
    },
    module:{
        rules:[
            {
                test: /\.(js|jsx)$/,
                exclude: /node_modules/,
                use:{
                    loader: "babel-loader"
                }
            },
            {
                test: /\.html$/,
                use:[
                    {
                        loader: "html-loader"
                    }
                ]
            }
        ]
    },
    plugins:[
        new HtmlWebPackPlugin({
            template: './public/index.html',
            filename: './index.html'

        }),
    ]
};

"scripts": {
    "build": "webpack --mode production"
  },
```

## Parte 9 - INSTALACION Y CONFIGURACION DE ENTORNO:
crear entorno de desarrollo local para ir probando lo que estamos construyecto

instalar como dependencia de desarrollo:
npm install --save-dev webpack-dev-server

Crearemos un script en el archivo de configuracion (package.json) para poder correr nuestro entorno de desarrollo local
```
{
  ""scripts"": {
    ""build"": ""webpack --mode production"",
    ""start"": ""webpack-dev-server --open --mode development""
  },
}
```
***NOTA: version nueva de webpack se cambia el codigo: => "start": "webpack serve --mode development --env development"***

se le pasa la configuracion de nuestro entorno local de desarrollo

Ahora para ejecutarlo vamos a terminal y corremos con npm run start (es el nombre del script que creamos)

con esto cada vez que se detecte un cambio se auto compilara el proyecto. (basicamente podremos probar en tiempo real)


## Estilos con SASS

preprocesador de CSS, para trabajar con variables en css y mixing
primero debemos instalar algunos paquetes:

npm install --save-dev mini-css-extract-plugin css-loader node-sass sass-loader

mini-css-extract-plugin => extraer css del bundle para crear un nuevo archivo de css
node-sass sass-loader => añade a compatibilidad con sass
css-loader => para cargar css

en el archivo de webpack tenemos que agregar una nueva regla para el css:
en test ponemos las extensiones de los arhivos a usar y en use los loader que ocuparemos. usaremos un loader para minificar el proyecto.
```
module: {
  rules: [
    {
      test: /\.(s*)css$/,
      use: [
        { loader: MiniCssExtractPlugin.loader },
        'css-loader',
        'sass-loader',
      ],
    }, 
  ],
},
```
en el archivo debemos crear una constante la referencia para el pugling que extrae css del proyecto:
```
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
```
ahora al final del archivo agregamos el nuevo pluging y el nombre.
```
plugins: [
  new MiniCssExtractPlugin({
    filename: 'assets/[name].css',
  }),
],
```
creamos la carpeta donde tendremos nuestros archivos de Estilos
assets sera la carpeta para estilos o recursos visuales, dentro de esta existe la carpeta styles, aqui tendremos los archivos de estilos (scss)
aqui debemos usa scss o css.

este archivo lo importamos a nuestro archivo de componente.
***NOTA: Ojo con los niveles de las carpetas***

ahora corremos el entorno de desarrollo local con npm run start.

## Configuracion final: ESLINT y GIT IGNORE
con esto podremos ver los errores al momento de tipear codigo y con git ignore podremos omitir archivos a subir a git:
```
npm install --save-dev eslint babel-eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-react eslint-plugin-jsx-a11y
```

- eslint-config-airbnb => usaremos las reglas de ellos para el proyecto
- eslint-plugin-react => para revisar codigo de react
- eslint-plugin-jsx-a11y => para accesibilidad de los proyecto y detectar lo que sea necesario para el navegador

ahora se necesita agregar la configuracion par eslint (archivo adjunto en esta carpeta)
con el nombre .eslintrc
aqui lo que estamos haciendo es crear un entorno con variables necesarias, con las configuracion necesarias y reglas para usar eslint.

con el achivos de gitignore realizamos el mismo proceso, creamos un archivo llamada .gitignore

