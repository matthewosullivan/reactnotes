# react notes
## 1

* Webpack
* Babel
* NPM scripts
* jest - unit testing
* ESlint - static analysis
* Prettier - formatting
* react-axe
* React's StrictMode 
* default ErrorBoundary component
* Create React App

## 2

initialise an NPM project
```
$ mkdir helloworld
$ cd helloworld
$ npm init
$ npm init -y # -y flag to use defaults
```
* package name - by default use directory name
* version - by default 1.0.0
* description
* entry point - default index.js
* test command
* git repository
* keywords
* author
* license - default ISC

package.json

```
{
  "name": "helloworld",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```
Initialize Git repository
```
$ cd helloworld
$ git init
$ git status
$ git add package.json
$ git status
$ git commit -m "initial commit"
$ git status
$ git log
```

## 3
Add project and push changes to github
```
$ git remote -v # show list of remote repos
$ git remote add origin https://github.com/matthewosullivan/helloworld.git
$ git remote -v
$ git push -u origin master
$ git status
$ git add readme.md
$ git status
$ git commit -m "Added a readme"
$ git status
$ git push
$ npm init -y # -y default 
```
package.json
```
{
  "name": "helloworld",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "repository": {
    "type": "git",
    "url": "git+https://github.com/matthewosullivan/helloworld.git"
  },
  "keywords": [],
  "bugs": {
    "url": "https://github.com/matthewosullivan/helloworld/issues"
  },
  "homepage": "https://github.com/matthewosullivan/helloworld#readme"
}
```
```
$ git status
$ git add package.json
$ git commit -m "Updated package.json"
$ git status
$ git push
```
## 4

```
$ cd helloworld
$ mkdir src
$ cd src
$ touch index.js
```
index.js:
```
console.log('Hello world')
```
Install webpack and webpack-cli
```
$ cd helloworld
$ npm install --save-dev webpack webpack-cli # --save-dev save as development dependency
```
modified package.json file, new package-lock.json file, new node_modules directory 

package.json:
```
"devDependencies": {
    "webpack": "^4.35.3",
    "webpack-cli": "^3.3.5"
  }
```
node_modules/.bin/webpack and node_modules/.bin/webpack-cli

```
$ node_modules/.bin/webpack
```
webpack creates dist/main.js minified file
```
$ node dist/main.js
```
package.json:
```
"scripts": {
    "build": "webpack",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

```
$ npm run build
```
src/greet.js
```
const greeting = 'Hello world'
export default greeting
```
src/index.js
```
import greeting from './greet'
console.log(greeting)
```
Terminal
To pass flag through npm script, put two hyphens, space, pass flag that goes into webpack
```
$ npm run build -- --mode development 
$ git status
```
dist is generated by webpack
node_modules from npm install
.gitignore
```
dist
node_modules
```
Terminal
```
$ git status
$ git add .
$ git status
$ git commit -m "Installed webpack"
$ git status
$ git push
```
## 5
Configure webpack

```
$ cd helloworld
$ touch webpack.config.js
```
webpack.config.js
```
const path = require('path')

module.exports = {
    entry: './src/index.js',
    output: {
        path: path.join(__dirname, 'dist'),
        filename: 'app.bundle.js'
    }
}
```
```
$ rm -rf dist
$ npm run build
```
dist/app.bundle.js

## 6
webpack mode setting 

webpack.config.js
development
```
const path = require('path')

module.exports = {
    mode: 'development',
    ...
}
```
webpack.config.js
production
```
const path = require('path')

module.exports = {
    mode: 'production',
    ...
}
```
Terminal
```
npm run build -- --mode development
npm run build # use configured default of production
```
## 7

Babel - modern javascript features

Change greet.js:
```
const getGreeting = (name) => `Hello ${name}`

export default getGreeting
```
Change index.js
```
import getGreeting from './greet'

console.log(getGreeting('world'))
```

```
$ npm run build
$ node dist/app.bundle.js
```
Install babel
Need compiler, transform new style JavaScript into JavaScript that will run in older browser - use Babel for this
-D shorthand for --save-dev
```
$ npm i -D @babel/core @babel/cli @babel/preset-env
```
Run babel
```
$ node_modules/.bin/babel
$ $(npm bin)/babel ./src/greet.js # does nothing
$ $(npm bin)/babel ./src/greet.js --presets=@babel/preset-env # converts to javascript that will run in older browers
```

Babel take modern JavaScript, convert it to Abstract Syntax Tree (AST) and spit out JavaScript that will run in all browsers.

## 8

Babel - compile modern JavaScript into JavaScript run in all browsers
webpack - bundle Javascript

Configure to work together
```
$ npm i -D babel-loader
```

webpack.config.js 

configure loaders to pass source code through before bundled for distribution

configure loader

```
module: {
        rules: [
            {
                test: /\.js$/,
                loader: 'babel-loader',
                exclude: /node_modules/,
                options: {
                    presets: ['@babel/preset-env']
                }
            }
        ]
    }
```

```
$ npm run build
```
Webpack has used babel-loader to transform our code before creating output bundle

## 9

React application

Install react react-dom prop-types as runtime dependencies

```
$ npm i -S react react-dom prop-types
```
package.json
```
  "dependencies": {
    "prop-types": "^15.7.2",
    "react": "^16.8.6",
    "react-dom": "^16.8.6"
  }
```
