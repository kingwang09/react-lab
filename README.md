# react-lab Start
### 1) install NPM install
sudo npm install -g webpack webpack-dev-server

npm install --save react react-dom

npm install --save-dev babel-core babel-loader babel-preset-es2015 babel-preset-react

npm install --save-dev react-hot-loader webpack webpack-dev-server


### 2) %PROJECT_HOME%/webpack.config.js

     var webpack = require("webpack");

     module.exports = {
          entry : './src/index.js',

          output : {
               path: __dirname + '/public',
               filename : 'bundle.js'
          },

          devServer : {
               hot: true,
               inline: true,
               host : '0.0.0.0',
               port: 4000,
               contentBase : __dirname + '/public/'
          },

          module : {
               loaders : [
                    {
                         test : /\.js$/,
                         //loaders: ['react-hot', 'babel?'+JSON.stringify({
                         //     cacheDirectory : true,
                         //     presets: ['es2015', 'react']
                         //})],
                         loader : 'babel',
                         query:{
                           cacheDirectory : true,
                           presets:['es2015', 'react']
                         },
                         exclude : /node_modules/
                    }
               ]
          },

          plugins : [
               new webpack.HotModuleReplacementPlugin()
          ]
     };


### 3) %PROJECT_HOME%/public/index.html 
     <div id="root"></div>
     <script src="bundle.js"></script>


### 4) %PROJECT_HOME%/src/components/App.js
     import React from 'react';

     class App extends React.Component{
          render(){
               return (
                <h1>Hello</h1>    
               );
          }
     }

     export default App;


### 5) %PROJECT_HOME%/src/index.js
     import React from 'react';
     import ReactDOM from 'react-dom';
     import App from './components/App';

     const rootElement = document.getElementById("root");
     ReactDOM.render( <App />, rootElement );


### 6) %PROJECT_HOME%/package.json
     scripts: {
     "dev-server" : "webpack-dev-server"
}
*npm run dev-server 로 실행 가능
