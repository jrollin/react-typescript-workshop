# React stack setup (cheatsheet)

- React with Typescript
- Prettier for common code formatting
- ESLint for common rules and syntax check

## Create react app

```bash
npx create-react-app talanlabs-react-ts --template typescript
```

```bash
npm start
```

> You should see the react logo spining on your localhost 

```
npm run test
```
> you should have a test running



## Eslint

```bash
yarn add eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-react --dev
```

.eslintrc.js

```javascript
module.exports = {
  parser: "@typescript-eslint/parser", // Specifies the ESLint parser
  extends: [
    "plugin:react/recommended", // Uses the recommended rules from @eslint-plugin-react
    "plugin:@typescript-eslint/recommended", // Uses the recommended rules from @typescript-eslint/eslint-plugin
  ],
  parserOptions: {
    ecmaVersion: 2018, // Allows for the parsing of modern ECMAScript features
    sourceType: "module", // Allows for the use of imports
    ecmaFeatures: {
      jsx: true, // Allows for the parsing of JSX
    },
  },
  rules: {
    // Place to specify ESLint rules. Can be used to overwrite rules specified from the extended configs
    // e.g. "@typescript-eslint/explicit-function-return-type": "off",
  },
  settings: {
    react: {
      version: "detect", // Tells eslint-plugin-react to automatically detect the version of React to use
    },
  },
};
```


## Prettier

```bash
yarn add prettier eslint-config-prettier eslint-plugin-prettier --dev
```

.prettiercs.js

```javascript
module.exports = {
  semi: true,
  trailingComma: "all",
  singleQuote: true,
  printWidth: 120,
  tabWidth: 4,
};
```


## Vscode debug 

Then add the block below to your launch.json file and put it inside the .vscode folder in your app’s root directory.

```javascript
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Chrome",
      "type": "chrome",
      "request": "launch",
      "url": "http://localhost:3000",
      "webRoot": "${workspaceFolder}/src",
      "sourceMapPathOverrides": {
        "webpack:///src/*": "${webRoot}/*"
      }
    }
  ]
}

```

## JSX

* no required !
* prevent XSS injection



JSX component

```javascript
<MyButton color="blue" shadowSize={2}>
  Cliquez ici
</MyButton>
```

Related element 

```javascript
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Cliquez ici'
)
```




### Attribute Expression vs string value


Use quotes (for string values)

```javascript
const element = <div tabIndex="0"></div>;
```

curly braces (for expressions), 

```javascript
const element = <img src={user.avatarUrl}></img>;
```




### JSX vs HTML

Looks like HTML but it is not !

=> used camelCase property


* class => className
* tabindex => tabIndex

