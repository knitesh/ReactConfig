# ReactConfig
 A starter React webpack and babel based configuration, supports hot module reloading.

To start a new app:-

Add Package.json and webpack.config.json to your master folder and run below commands.

### Install WebPack and Webpack-dev-server by running below commands
* $npm install webpack -g
* $npm install webpack-dev-server -g

### Install all node modules
* $npm install

### To run your app

* $npm run start-webpack-server

### Package.json
```
{
    "name": "sample-react-webpack-package",
    "version": "0.1.0",
    "description": "Simple Package.json configuration for React App suppporting webpack and babel.",
    "main": "./sample-app/server.js",
    "private": true,
    "scripts": {
        "start-webpack-server": "webpack-dev-server --hot --inline --colors --progress",
        "start": "node ./sample-app/server.js"
    },
    "repository": {
        "type": "git",
        "url": "git+https://github.com/knitesh/ReactConfig.git"
    },
    "keywords": [
    "react",
    "knitesh",
    "redux",
    "sample-app"
  ],
    "author": "Kumar Nitesh",
    "license": "MIT",
    "bugs": {
        "url": "https://github.com/knitesh/ReactConfig/issues"
    },
    "homepage": "https://github.com/knitesh/ReactConfig#readme",
    "dependencies": {
        "botbuilder": "^0.9.2",
        "express": "^4.13.4",
        "jquery": "^2.2.3",
        "react": "^15.0.2",
        "react-addons-pure-render-mixin": "^15.0.2",
        "react-dom": "^15.0.2",
        "react-router": "^2.4.0",
        "restify": "^4.0.4"
    },
    "devDependencies": {
        "babel-core": "^6.8.0",
        "babel-loader": "^6.2.4",
        "babel-preset-es2015": "^6.6.0",
        "babel-preset-react": "^6.5.0",
        "css-loader": "^0.23.1",
        "file-loader": "^0.8.5",
        "react-hot-loader": "^1.3.0",
        "style-loader": "^0.13.1",
        "url-loader": "^0.5.7",
        "webpack": "^1.13.0"
    }
}

```

### webpack.config.json
```
var path = require('path');
var webpack = require('webpack');

module.exports = {
  context: path.join(__dirname, 'app'),
  entry: {
    javascript: './app.js',
    html: './index.html'
  },
  output: { 
    path: path.join(__dirname, 'dist'),
    filename: 'bundle.js'
  },
  module: {
    loaders: [
      {
        test: /.js?$/,
        loader: 'babel-loader',
        exclude: /node_modules/,
        query: {
          presets: ['es2015', 'react']
        }
      },
      {
        test: /\.html$/,
        loader: "file?name=[name].[ext]",
      },
      {
        test: /\.css$/, 
        loader: "style-loader!css-loader" 
      },
      { 
        test: /\.png$/, 
        loader: "url-loader?limit=100000" 
      },
      { 
        test: /\.jpg$/, 
        loader: "file-loader" 
      }
    ]
  },
  devServer: {
    historyApiFallback: true
  }
};
```
