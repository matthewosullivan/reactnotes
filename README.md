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

```
"scripts": {
    "build": "webpack",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

```
$ npm run build
```
