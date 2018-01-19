# Basic React Setup: 

Once you have your folder created begin by running to instantly initialize your project. The -y flag on the npm init command will automatically populate all options with the default npm init values.

```
yarn init -y 
```

## Install webpack and dependencies: 

Webpack is a static module bundler for JavaScript applications.

The webpack-dev-server is a little Node.js Express server, which uses the webpack-dev-middleware to serve a webpack bundle.

```
yarn add webpack webpack-dev-server path
```

Create the webpack.config.js file.

```
touch webpack.config.js
```


Add the following to your webpack.config.js to create an entry point and an output to get a running instance of webpack as well as loaders because we want the browser we use to be able to interprate and run JSX code and code written in ES6.

The entry specifies the entry file where the bundler starts the bundling process.

The output specifies the location where the bundled Javascript code is to be saved.

The loaders are transformations that are applied on a file in our app. At a high level, loaders have two purposes in your webpack configuration:

1. The test property identifies which file or files should be transformed.

2. The use property indicates which loader should be used to do the transforming.

```
const path = require('path');

const HtmlWebpackPlugin = require('html-webpack-plugin');
const HtmlWebpackPluginConfig = new HtmlWebpackPlugin({
  template: './public/index.html',
  filename: 'index.html',
  inject: 'body'
})

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve('dist'),
    filename: 'index_bundle.js'
  },
  module: {
    loaders: [
      { test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ },
      { test:/\.css$/, use:['style-loader','css-loader']}
    ]
  },
  plugins: [HtmlWebpackPluginConfig]
}


```


Install the following:


```
yarn add babel-loader css-loader  style-loade babel-core babel-preset-es2015 babel-preset-react --dev
```

Add a .babelrc file: 

```
touch .babelrc
```

Add into your .babelrc file the following: 

```
{
    "presets":[
        "es2015", "react"
    ]
}
```

Create public and src folders. Inside the public folder add an index.html file. Inside the src folder add a index.js file.

```
mkdir public
mkdir src
touch index.js
touch index.html
```

Add the following to your index.html file: 

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>React App Setup</title>
  </head>
  <body>
    <div id="root">

    </div>
  </body>
</html>
```

Install the following: 

```
yarn add html-webpack-plugin react react-dom
```

In your package.json add: 

```
  "scripts": {
    "start": "webpack-dev-server"
  },
```

Then create a component: 

```
cd src
mkdir components 
cd components
touch App.js
```

In your App.js add: 

```
import React, {Component} from 'react';
import './App.css';

export default class App extends Component {
  render() {
    return (
     <div>
        <h1>Testing</h1>
      </div>
    );
  }
}
```

In your index.js: 

```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './components/App.js';

ReactDOM.render(
    <App />, 
document.getElementById('root'));
```

All done go ahead and test it out!

```
yarn start
```