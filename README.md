# @raul338/vue-cli-plugin-stylelint
forked from @zysce/vue-cli-plugin-stylelint
forked from @samhammer/vue-cli-plugin-stylelint


> stylelint plugin for vue-cli

This allows you to use [stylelint-config-recommended-vue](https://github.com/ota-meshi/stylelint-config-recommended-vue)
with [SCSS (recommended)](stylelint-config-recommended-scss) and/or [prettier](https://github.com/prettier/stylelint-prettier#recommended-configuration)

## Injected commands

- **`vue-cli-service lint:style`**

  ```
  Usage: vue-cli-service lint:style [options] [...files]

  Options:

    --no-fix           do not auto-fix errors
    --options          list additional stylelint cli options
  ```

  Lints and fixes files. If no specific files are given, it lints all vue files, html files, and stylesheets in `src`.

## Configuration (vue.config.js, "vue" in package.json)

Lint on (re)build with `stylelint-webpack-plugin` can be enabled with the `lintStyleOnBuild` option. You can also provide additional options to stylelint. See available options on the stylelint [website](https://stylelint.io/user-guide/node-api/#options).

```js
module.exports = {
  // ...
  pluginOptions: {
    lintStyleOnBuild: true,
    stylelint: {
      fix: true, // boolean (default: true)
      files: "", // string | [string] (default: ['src/**/*.{vue,htm,html,css,sss,less,scss}'])
      // See https://stylelint.io/developer-guide/formatters/
      formatter: () => {}, // function (default: require('stylelint-codeframe-formatter'))
      // etc...
    },
  },
};
```

## Installing in an already created project

via vue-cli (recommended)

```
vue add @raul338/vue-cli-plugin-stylelint
```

via yarn

```
yarn add -D @raul338/vue-cli-plugin-stylelint
vue invoke @raul338/vue-cli-plugin-stylelint
```

via npm

```
npm install --save-dev @raul338/vue-cli-plugin-stylelint
vue invoke @raul338/vue-cli-plugin-stylelint
```

## webpack-chain Injections

- `config.plugin('stylelint')`
- `config.plugin('stylelint').use('stylelint-webpack-plugin')`
- `config.plugin('friendly-errors').tap(/* Adds additional transformer and formatter */)`
