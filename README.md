# js-yaml-loader for Webpack

[JS-YAML](https://github.com/nodeca/js-yaml) loader for webpack.

## Installation

`yarn add js-yaml-loader`

## Usage

[Webpack documentation](https://webpack.js.org/concepts/loaders/#using-loaders)

``` javascript
import doc from 'js-yaml-loader!./file.yml';
// => returns a javascript object. see https://github.com/nodeca/js-yaml
```

``` javascript
// webpack.config.js
module: {
  rules: [{
    test: /\.yaml$/,
    use: 'js-yaml-loader',
  }]
}
```

## Loader options

### safe *(boolean) (default=true)*

Use [`safeLoad`](https://github.com/nodeca/js-yaml#safeload-string---options-) instead of [`load`](https://github.com/nodeca/js-yaml#load-string---options-). Set `safe` to `false` to allow unsafe types to load, such as regular expressions, functions, and `undefined`.

### Difference from [yaml-loader](https://github.com/okonet/yaml-loader)

[yaml-loader](https://github.com/okonet/yaml-loader) loads YAML files
as _JSON_ and is commonly used in conjuction with
[json-loader](https://github.com/webpack-contrib/json-loader).

In contrast, this loader loads YAML files as JavaScript objects using
the [un-eval](https://github.com/tiansh/un_eval.js) library. This allows YAML value types otherwise
disallowed in JSON such as `Infinity`, `RegExp`, `Function`, etc.
[See js-yaml's supported YAML types](https://github.com/nodeca/js-yaml#supported-yaml-types)

## License

[MIT](http://www.opensource.org/licenses/mit-license.php)
