# api documentation for  [buble (v0.15.2)](https://gitlab.com/Rich-Harris/buble#README)  [![npm package](https://img.shields.io/npm/v/npmdoc-buble.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-buble) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-buble.svg)](https://travis-ci.org/npmdoc/node-npmdoc-buble)
#### The blazing fast, batteries-included ES2015 compiler

[![NPM](https://nodei.co/npm/buble.png?downloads=true)](https://www.npmjs.com/package/buble)

[![apidoc](https://npmdoc.github.io/node-npmdoc-buble/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-buble_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-buble/build/apidoc.html)

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
            "name": "marijn",
            "email": "marijnh@gmail.com"
        },
        {
            "name": "rich_harris",
            "email": "richard.a.harris@gmail.com"
        }
    ],
    "name": "buble",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module buble](#apidoc.module.buble)
1.  [function <span class="apidocSignatureSpan">buble.</span>target ( target )](#apidoc.element.buble.target)
1.  [function <span class="apidocSignatureSpan">buble.</span>transform ( source, options )](#apidoc.element.buble.transform)
1.  string <span class="apidocSignatureSpan">buble.</span>VERSION



# <a name="apidoc.module.buble"></a>[module buble](#apidoc.module.buble)

#### <a name="apidoc.element.buble.target"></a>[function <span class="apidocSignatureSpan">buble.</span>target ( target )](#apidoc.element.buble.target)
- description and source-code
```javascript
function target( target ) {
	var targets = Object.keys( target );
	var bitmask = targets.length ?
		2147483647 :
		1073741824;

	Object.keys( target ).forEach( function ( environment ) {
		var versions = matrix[ environment ];
		if ( !versions ) throw new Error( ("Unknown environment '" + environment + "'. Please raise an issue at https://gitlab.com/Rich
-Harris/buble/issues") );

		var targetVersion = target[ environment ];
		if ( !( targetVersion in versions ) ) throw new Error( ("Support data exists for the following versions of " + environment + ": " + (
Object.keys( versions ).join( ', ')) + ". Please raise an issue at https://gitlab.com/Rich-Harris/buble/issues") );
		var support = versions[ targetVersion ];

		bitmask &= support;
	});

	var transforms = Object.create( null );
	features.forEach( function ( name, i ) {
		transforms[ name ] = !( bitmask & 1 << i );
	});

	dangerousTransforms.forEach( function ( name ) {
		transforms[ name ] = false;
	});

	return transforms;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.buble.transform"></a>[function <span class="apidocSignatureSpan">buble.</span>transform ( source, options )](#apidoc.element.buble.transform)
- description and source-code
```javascript
function transform( source, options ) {
	if ( options === void 0 ) options = {};

	var ast;

	try {
		ast = parse( source, {
			ecmaVersion: 7,
			preserveParens: true,
			sourceType: 'module',
			plugins: {
				jsx: true,
				objectSpread: true
			}
		});
	} catch ( err ) {
		err.snippet = getSnippet( source, err.loc );
		err.toString = function () { return ((err.name) + ": " + (err.message) + "\n" + (err.snippet)); };
		throw err;
	}

	var transforms = target( options.target || {} );
	Object.keys( options.transforms || {} ).forEach( function ( name ) {
		if ( name === 'modules' ) {
			if ( !( 'moduleImport' in options.transforms ) ) transforms.moduleImport = options.transforms.modules;
			if ( !( 'moduleExport' in options.transforms ) ) transforms.moduleExport = options.transforms.modules;
			return;
		}

		if ( !( name in transforms ) ) throw new Error( ("Unknown transform '" + name + "'") );
		transforms[ name ] = options.transforms[ name ];
	});

	return new Program( source, ast, transforms, options ).export( options );
}
```
- example usage
```shell
...
buble input.js > output.js
'''

...or via the JavaScript API:

'''js
var buble = require( 'buble' );
var result = buble.transform( source ); // { code: ..., map: ... }
'''


## License

MIT
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
