# nodupdeps (No Duplicate Dependencies)

CLI that ensures that there is only a single version of a dependency installed.

## Why?

I want to use nconf for my config, but I also want to write tons of small modules that share that configuration. If I'm not super careful about specifying semver compatible versions, and running `npm dedupe`, I could easily load two versions of nconf that don't share the configuration.

## How?

```bs
npm install -g nodupdeps
```
```js
nodupdeps [packageName ...]
```

## When?

I'd add a post install hook!

> package.json

```json
{
  ...
  "scripts": {
    "postinstall": "nodupdeps"
  },
  "devDependencies": {
    "nodupdeps": "*"
  },
  ...
}
```

## Examples

> \> nodupdeps source-map lodash

```bs
Error: Duplicates found.

source-map
   node_modules/babel/node_modules/source-map
   node_modules/babel-core/node_modules/source-map
   node_modules/babel-core/node_modules/source-map-support/node_modules/source-map
   node_modules/css-loader/node_modules/postcss/node_modules/source-map
   node_modules/eslint/node_modules/handlebars/node_modules/source-map
   node_modules/eslint/node_modules/handlebars/node_modules/uglify-js/node_modules/source-map
   node_modules/isparta-loader/node_modules/isparta/node_modules/escodegen/node_modules/source-map
   node_modules/isparta-loader/node_modules/isparta/node_modules/istanbul/node_modules/handlebars/node_modules/source-map
   node_modules/isparta-loader/node_modules/isparta/node_modules/istanbul/node_modules/handlebars/node_modules/uglify-js/node_modules/source-map
   node_modules/isparta-loader/node_modules/isparta/node_modules/source-map
   node_modules/karma/node_modules/source-map
   node_modules/karma-coverage/node_modules/istanbul/node_modules/escodegen/node_modules/source-map
   node_modules/karma-coverage/node_modules/istanbul/node_modules/handlebars/node_modules/source-map
   node_modules/karma-coverage/node_modules/istanbul/node_modules/handlebars/node_modules/uglify-js/node_modules/source-map
   node_modules/karma-coverage/node_modules/source-map
   node_modules/karma-webpack/node_modules/source-map
   node_modules/react/node_modules/envify/node_modules/jstransform/node_modules/source-map
   node_modules/webpack/node_modules/uglify-js/node_modules/source-map
   node_modules/webpack/node_modules/webpack-core/node_modules/source-map

lodash
   node_modules/babel/node_modules/lodash
   node_modules/babel-core/node_modules/lodash
   node_modules/css-loader/node_modules/cssnano/node_modules/postcss-svgo/node_modules/svgo/node_modules/js-yaml/node_modules/argparse/node_modules/lodash
   node_modules/eslint/node_modules/inquirer/node_modules/lodash
   node_modules/eslint/node_modules/js-yaml/node_modules/argparse/node_modules/lodash
   node_modules/isparta-loader/node_modules/isparta/node_modules/istanbul/node_modules/js-yaml/node_modules/argparse/node_modules/lodash
   node_modules/karma/node_modules/lodash
   node_modules/karma-coverage/node_modules/istanbul/node_modules/js-yaml/node_modules/argparse/node_modules/lodash
   node_modules/karma-webpack/node_modules/lodash
```
