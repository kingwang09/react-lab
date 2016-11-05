# react-lab Start
### install NPM install
sudo npm install -g webpack webpack-dev-server

npm install --save react react-dom

npm install --save-dev babel-core babel-loader babel-preset-es2015 babel-preset-react

npm install --save-dev react-hot-loader webpack webpack-dev-server

### %PROJECT_HOME%/webpack.config.js

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

