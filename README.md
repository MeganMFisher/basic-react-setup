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
module.exports = {
  entry: './public/index.js',
  output: {
    path: path.resolve('dist'),
    filename: 'index_bundle.js'
  },
  module: {
    loaders: [
      { test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ },
      { test:/\.css$/, use:['style-loader','css-loader']}
    ]
  }
}
```





```
yarn add babel-loader css-loader  style-loade babel-core babel-preset-es2015 babel-preset-react --dev
```


```
touch .babelrc
```



```
mkdir public
mkdir src
touch index.js
touch index.html
```

```
yarn add html-webpack-plugin
```

```
yarn add react react-dom
```

```
cd src
mkdir components 
cd components
touch App.js
```