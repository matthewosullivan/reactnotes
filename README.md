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
