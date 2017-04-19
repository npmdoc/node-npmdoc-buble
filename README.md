# npmdoc-buble

#### api documentation for  [buble (v0.15.2)](https://gitlab.com/Rich-Harris/buble#README)  [![npm package](https://img.shields.io/npm/v/npmdoc-buble.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-buble) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-buble.svg)](https://travis-ci.org/npmdoc/node-npmdoc-buble)

#### The blazing fast, batteries-included ES2015 compiler

[![NPM](https://nodei.co/npm/buble.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/buble)

- [https://npmdoc.github.io/node-npmdoc-buble/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-buble/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-buble/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-buble/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-buble/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-buble/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Rich Harris"
    },
    "bin": {
        "buble": "./bin/buble"
    },
    "bugs": {
        "url": "https://gitlab.com/Rich-Harris/buble/issues"
    },
    "dependencies": {
        "acorn": "^3.3.0",
        "acorn-jsx": "^3.0.1",
        "acorn-object-spread": "^1.0.0",
        "chalk": "^1.1.3",
        "magic-string": "^0.14.0",
        "minimist": "^1.2.0",
        "os-homedir": "^1.0.1"
    },
    "description": "The blazing fast, batteries-included ES2015 compiler",
    "devDependencies": {
        "buble": "0.8.2",
        "console-group": "^0.2.1",
        "eslint": "^2.10.1",
        "glob": "^7.0.3",
        "mocha": "^2.4.5",
        "regexpu-core": "^2.0.0",
        "rimraf": "^2.5.2",
        "rollup": "^0.26.3",
        "rollup-plugin-buble": "^0.8.0",
        "rollup-plugin-commonjs": "^2.2.1",
        "rollup-plugin-json": "^2.0.0",
        "rollup-plugin-node-resolve": "^1.5.0",
        "source-map": "^0.5.6",
        "source-map-support": "^0.4.0"
    },
    "directories": {},
    "dist": {
        "shasum": "547fc47483f8e5e8176d82aa5ebccb183b02d613",
        "tarball": "https://registry.npmjs.org/buble/-/buble-0.15.2.tgz"
    },
    "files": [
        "bin",
        "src",
        "dist",
        "register.js",
        "README.md"
    ],
    "gitHead": "f6b9b9dd3e78dd54775a98c862002e17fc4a7ca2",
    "homepage": "https://gitlab.com/Rich-Harris/buble#README",
    "jsnext:main": "dist/buble.es.js",
    "keywords": [
        "javascript",
        "transpilation",
        "compilation",
        "esnext",
        "es2015",
        "es2017",
        "es6",
        "es7"
    ],
    "license": "MIT",
    "main": "dist/buble.umd.js",
    "maintainers": [
        {
            "name": "marijn"
        },
        {
            "name": "rich_harris"
        }
    ],
    "name": "buble",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://gitlab.com/Rich-Harris/buble.git"
    },
    "scripts": {
        "build": "npm run build:umd && npm run build:es && npm run build:browser",
        "build:browser": "rollup -c --environment DEPS -f umd -o dist/buble.deps.js",
        "build:es": "rollup -c -f es6 -o dist/buble.es.js",
        "build:umd": "rollup -c -f umd -o dist/buble.umd.js",
        "lint": "eslint src",
        "prepublish": "npm test && npm run build:es",
        "pretest": "npm run build:umd && npm run build:browser",
        "pretest:node": "npm run build:umd",
        "test": "mocha test/test.js --compilers js:./register",
        "test:node": "mocha test/test.js --compilers js:./register"
    },
    "version": "0.15.2"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
