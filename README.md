# apuntesReact
notas de curso react
Creacion de nueestro sitio wev usando la plantilla por defecto de create-react-app:
npx create-react-app nombre-de-tu-proyecto

Iniciar el servidor de desarrollo:
npm start


esto se instala en una carpeta todo el proyecto funciona con esto sin esto no arranca

NOTA
buscar que era npx

al ejecutar npm start la terminal muestra la ip y se despliega el sitio web basico de react

node_modules -> son las (elemetos) librerias que usa react, nunca sube a produccion
public -> archivos publicos, para subir a producción (archivo favicon.icon, manifest.json) aqui se encuentra nuestro archivo index.html principal, aqui esta el dom
src -> aqui esta toda la aplicacion (serviceWorker.js => escucha los cambios en nuestra aplicacion), los archivos de js, css, sass, jsx

.gitignore

package.json -> contiene toda la informacion  y configuracion de nuestro proyecto

README.md


create carpeta para componentes dentro de src:

primer componente a crear sera un Stateful.js (Capitalcase)

import dentro del archivos Libreria de react:

Stateful debe extender de Components (libreria de react)

crear constructor en la clase Stateful y funcion render() (retorna la funcion la pagina)

exportar la clase.

crear un Stateless.js

import react library

create constants Stateless as a function and return html into -> ()

export function

crear un Presentacional.js

importar react

crear constante como funcion y retorna html entre parentesis (usar arrow function)

exporta constante


Stateful -> se encarga manejar los ciclos de vida eventos y los estados de los elementos,es una clase

Stateless -> no depende de tener un estado o un ciclo de vida solo presenta logica, son funciones, solo lo que necesitamos.

Presentacionales -> no tienen logica ni propiedades se encargan de mostrar el html, de como se vera los elementos, tienen una parte particular de html usa funciones pero no logica.(averiguar mas)

parte 2:

JSX -> sintaxis que usa react para mezclar javascripts html y css en un solo componente

para usarlo se crea un archivo en componentes con extension jsx (igual se puede usar la extension js).
para los elementos de la clase los HTML debe reemplazar el class por className
para añadir el contenido (como el valor de una variable) del elemento de html se usan -> {} en el elemento html
se deben cerrar todas las etiquetas (HTML)
podemos hacer validaciones (como un if ternario) dentro del return de la funcion, en el html

para visualizar el componente creado en el sitio se debe conectar a la aplicacion en el archivos index.js, donde se encuentra la configuracion del proyecto, aqui tenemos react y reactDOM, archivo de css, y otros componentes.
Aqui debemos importar el componente que se creo nuevo.

no es necesario al importar especificar la extension de los archivos.

para mostrar el componente importado se debe agregar en los parentesis de la funcion render del ReactDOM.
Ejemplo:
ReactDOM.render(<HolaMundo /> ---> este es el componente, document.getElementById('root'));

Parte 3:

Podemos pasar propiedades a nuestros componentes asi como lo hacemos en las funciones, no importa si es presentacional o de tipo clase, pero si necesitas manipularlas es necesario instanciarlas en una nueva variable.

Ejemplo:
const Button = props => { return HTML AQUI! props.value}

una vez creado el componente se agrega al archivo index.js y dentro del mismo se le puede pasar las propiedades.
Ejemplo:
ReactDOM.render(<Button text="Click!" /> ---> este es el componente y la propiedad, document.getElementById('root'));

tambien puedes desestructurar los datos, extraer el valor del valor dentro de props.

Ejemplo:
const { value1, value2 } = props

Parte 4:

Metodos del ciclo de vida (similares a los de android):

Fases de los componentes de react:
Montaje => Constructor, render, ComponentDidMount
Actualizacion => getDerivedStateFromProps, shouldComponentUpdate, render, componentDidUpdate
Desmontaje => componentWillUnmont
Manejo de Errores => getDerivedStateFromError, componentDidCatch


Parte 5:

los componentes Stateful son clases que extienden de React.Components (puedes extender desde el import o desde la misma clase)
dentro de la clase usas la funcion render y esta funcion retorna el html.

El estado en react es un objeto que le puedes definir variables de todo tipo y al que podemos acceder desde nuestro componente desde el momento en que se inicializa.
Ejemplo:
(detro de la clase) 
state = {
  count: 0,
}

este objeto lo podemos desestructurar dentro de la funcion render de la clase para usarlo en el html:
Ejemplo:
const { count } = this.state (siguiendo el ejemplo de arriba)

Eventos (html):
Deben usar camelCase

creamos una funcion para el ejemplo:

handleClick = () => ( this.setState({ count: this.state.count + 1 }));

esta funcion se la debemos asignar al evento onClick del elemento HTML:
onClick{this.handleClick}

Parte 6 - INSTALACION Y CONFIGURACION DE ENTORNO:
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

instalar react
npm install --save react react-dom

OJO CON LAS VULNERABILIDADES AL INSTALAR.

al instalar react se crea el archivos package-lock.json, permite manejar el versionado de los paquetes que instales
en el archivo package.json se agregan las dependencias de react y ReactDOM.

Parte 7 - INSTALACION Y CONFIGURACION DE ENTORNO:
creamos archivo index.js en la raiz de la carpeta src
aqui importamos react y ReactDOM

utilizamos ReactDOM para pasar el componente por medio del metodo render
tenemos que importar el componente

render recibe dos elementos, el componente y donde voy a empujar el componente (la parte el html)

en el archivo de public le daremos vida a todo
creamos nuestra base de HTML (head, html, body, title...)
creamos un div le asignamos un id y ese id se envia al render de ReactDOM

Con babel podemos crear y convertir JavaScripts moderno en JavaScripts compati ble con todos los navegadores.

install babel:
npm install --save-dev @babel/core @babel/preset-env @babel/preset-react babel-loader

--save-dev => indica que es solo para desarrollo la dependencia

se crea el archivo .babelrc par la configuracion de BABEL, en la raiz del proyecto

aqui agregamos las configuracion de todo lo instalado de babel

@babel/core -> todas las herramientas para convertir a codigo moderno
@babel/preset-env 
@babel/preset-react 
babel-loader -> trabaja con webpack

creamos un objeto y le agregamos un arreglo llamado presents que contenga el nombre de los preset que se instalaron => @babel/preset-env @babel/preset-react 
uno ayuda a trabajar con ESMASCRIPT y el otro con jsx y react
Ejemplo:
{
  "presents": [
    "@babel/preset-env"
    "@babel/preset-react"
    ]
}

Parte 8 - INSTALACION Y CONFIGURACION DE ENTORNO:

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


Parte 9 - INSTALACION Y CONFIGURACION DE ENTORNO:
crear entorno de desarrollo local para ir probando lo que estamos construyecto
