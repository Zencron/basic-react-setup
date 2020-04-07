# basic-react-setup
Basic setup for react/webpack/babel

Initializing the project
```
npm init -y
```

Installing required dependencies:

  webpack webpack-cli // installs webpack

  webpack-dev-server // webpack's development server for hot-loading while programming

  react react-dom // installs react

  @babel/core babel-loader @babel/preset-env @babel/preset-react // installs babel and presets necessary for JSX

  html-webpack-plugin html-loader // webpack loader/plugin for html files

  style-loader css-loader // webpack loader for css files

```
npm i webpack webpack-cli webpack-dev-server react react-dom @babel/core babel-loader @babel/preset-env @babel/preset-react html-webpack-plugin html-loader style-loader css-loader --save-dev
```

webpack.config.js

```
const HtmlWebPackPlugin = require("html-webpack-plugin");
module.exports = {
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      },
      {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader"
          }
        ]
      },
      {
        test: /\.css$/,
        use: [ "style-loader" , "css-loader" ]
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: "./src/index.html",
      filename: "./index.html"
    })
  ]
};
```
.babelrc

```
{    
	"presets": ["@babel/preset-env" , "@babel/preset-react"]
}
```

Add scripts to package.json

```
"scripts": {
  "build": "webpack --mode production",
  "start": "webpack-dev-server --open --hot --mode development"
},
```

index.html

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Basic React Setup</title>
    </head>
    <body>
        <div id="root"></div>
    </body>
</html>
```

index.js

```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App.js';

const root = document.getElementById('root');
root ? ReactDOM.render(<App /> , root) : false;
```

