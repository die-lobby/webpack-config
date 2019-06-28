# Configs:

**install**
````bash
yarn add @pluswerk/webpack-config --dev
````
**package.json**
````json
{
  "scripts": {
    "build": "webpack --mode production --config node_modules/@pluswerk/webpack-config/webpack.config.js --hide-modules",
    "build:watch": "webpack --watch --mode production --config node_modules/@pluswerk/webpack-config/webpack.config.js --hide-modules",
    "build:dev": "webpack --mode development --config node_modules/@pluswerk/webpack-config/webpack.config.js --hide-modules",
    "build:dev:watch": "webpack --watch --mode development --config node_modules/@pluswerk/webpack-config/webpack.config.js --hide-modules",
    "serve": "webpack-dev-server --config node_modules/@pluswerk/webpack-config/webpack.hmr.config.js --mode development --colors --progress --inline --hide-modules"
  },
  "sideEffects": true
}
````

**build.settings.js**
````js
module.exports = {
  directory: {
    typescript: 'Typescript/',
    scss: 'Scss/',
    generated: 'Generated/',
  },
  entry: {
    main: ['./Typescript/index.ts', './Scss/index.scss']
  }
};
````

# Overwrite configs:
you can overwrite `tsconfig.json`, `tslint.json` and `stylelint.config.js` .
- Either name the file exactly the same and put it in the root directory.
- Or you can adjust the path in build.settings.js and put the file wherever you like.

# Options:
````js
module.exports = {
  directory: {
    typescript: 'Typescript/',
    scss: 'Scss/',
    generated: 'Generated/',
  },
  files: {
    tsConfig: './tsconfig.json',
    tsLint: './tslint.json',
    stylelint: './stylelint.config.js',
  },
  entry: {
    main: ['./Typescript/index.ts', './Scss/index.scss']
  },
  envPath: '.env',
  serverActiveEnv: 'NODE_ACTIVE=TRUE',
  serverInactiveEnv: 'NODE_ACTIVE=FALSE',
  // more info on definePlugin: https://webpack.js.org/plugins/define-plugin/
  definePlugin: {
    BOOLEAN_ENV: !!process.env.BOOLEAN_ENV,
    STRING_ENV: JSON.stringify(process.env.STRING_ENV),
  },
  webpackConfig: {},
}
````

#TODO:
- dosn't lint scss inside vue
- `sideEffects:true` https://github.com/vuejs/vuepress/issues/718

