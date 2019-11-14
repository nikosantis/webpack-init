# webpack inicial para desarrollo

## Iniciar proyecto
Considerar que este repositorio ya está preconfigurado y para iniciar el proyecto solo basta con poner en la terminal

`npm install`

Para correr servidor:

`npm run dev`

De todas maneras, aquí comento el paso a paso.

## Paso a paso para crear desde 0

Debes crear una carpeta /src y dentro poner un index.js

Iniciar el proyecto con

`npm init -y`

Se creará el archivo package.json que contiene las dependencias y configuraciones

Instalaremos webpack y webpack-cli como dependencias de desarrollo

`npm i webpack webpack-cli --save-dev`

Una vez instalado, usaremos webpack para crear una carpeta /dist y dentro un archivo de distribución de nuestro index.js usando la terminal.

`./node_modules/.bin/webpack src/index.js`

Mostrará algunos WARNING pero no pescar jiji
Es porque aún no le decimos en que ambiente estamos trabajando, desarrollo o producción.

Vamos a crear el archivo webpack.config.js y mientras instalaremos un plugin de webpack para exportar en HTML en vez de solo js.

`npm i html-webpack-plugin --save-dev`

La configuración del webpack.config.js es así:

    const HtmlWebpackPlugin = require
    ('html-webpack-plugin')
    
    module.exports = {
      output: {
        filename: 'app.bundle.js'
      },
      plugins: [
        new HtmlWebpackPlugin({
          template: 'src/index.html'
        })
      ]
    }


Luego en el archivo package.json agregaremos un nuevo script. En donde dice scripts aparecerá esto:

    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },


Y le agregaremos este nuevo script

    "scripts": {
        "build": "webpack",
        "test": "echo \"Error: no test specified\" && exit 1"
      },


Para probar este script vamos a la terminal:

`npm run build`

Y con la magia de webpack ahora se han creado dos archivos, el index.html y el app.bundle.js.

Después de esto, el main.js creado al inicio para demostrar qué hace webpack, se puede eliminar.

Ahora instalaremos el servidor de webpack

## Servidor de Webpack

Para instalarlo:

`npm i webpack-dev-server --save-dev`

Y vamos a crear otro script en package.json para finalizar.

Para probarlo se corre el comando:

`npm run dev`

Por defecto, el servidor correrá en:

http://localhost:8080/
