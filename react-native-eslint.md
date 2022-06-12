# Introduction

ESLint is a tool that allows us to maintain code quality and enforce code conventions. ESLint is a static code evaluator. Basically, it means that ESLint will not actually execute the code but will instead read through the source code to see if all the preconfigured code conventions are followed by the developers.

At [Osmosys Software Solutions Pvt Ltd](https://osmosys.co/) we standardize the ESLint configuration, which will be used across multiple projects.

# Prerequisite

React Native app with JavaScript or TypeScript

Any existing React Native app with JavaScript or TypeScript. If you don't have one, then you can create a basic React Native app using the following command.

> **Note**: for now assuming we will use React Native app with JS

```sh
npm react-native init my_app
```

React Native comes with a predefined ESLint config, but sometimes it doesn’t come with the latest ESLint version, so we’ll simply uninstall it and then install it again to pull the latest version.

```sh
npm uninstall eslint

# install the latest eslint package version
npm install eslint --save-dev
```

# Installation

Install the following packages:

- [eslint-plugin-react@latest](https://github.com/jsx-eslint/eslint-plugin-react)
- [@typescript-eslint/eslint-plugin@latest](https://github.com/typescript-eslint/typescript-eslint/tree/main/packages/eslint-plugin)
- [eslint-config-standard@latest](https://github.com/standard/eslint-config-standard)
- [eslint-plugin-import@^2.25.2](https://github.com/import-js/eslint-plugin-import)
- [eslint-plugin-n@^15.0.0 ](https://github.com/github/eslint-plugin-github)
- [eslint-plugin-promise@^6.0.0 ](https://github.com/xjamundx/eslint-plugin-promise)
- [@typescript-eslint/parser@latest](https://github.com/typescript-eslint/typescript-eslint/tree/main/packages/parser)
- [eslint-plugin-react-native](https://github.com/intellicode/eslint-plugin-react-native)

```sh
npm i eslint-plugin-react@latest, @typescript-eslint/eslint-plugin@latest, eslint-config-standard@latest, eslint@^8.0.1, eslint-plugin-import@^2.25.2, eslint-plugin-n@^15.0.0, eslint-plugin-promise@^6.0.0, @typescript-eslint/parser@latest eslint-plugin-react-native
```

# Configure ESLint

React Native comes with a predefined .eslintrc.js file in the root folder of your project, Open `.eslintrc.js` file and modify it like the below configuration.

```js
module.exports = {
  env: {
    browser: true,
    es2021: true,
    "react-native/react-native": true,
  },
  extends: ["plugin:react/recommended", "standard"],
  parser: "@typescript-eslint/parser",
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: "latest",
    sourceType: "module",
  },
  plugins: ["react", "react-native"],
  rules: {
    // allow .js files to contain JSX code
    "react/jsx-filename-extension": [1, { extensions: [".js", ".jsx"] }],
  },
};
```

# Usage

Add below scripts in your package.json to run lint on all files including .js and .tsx ones and to fix them.

```
{
  "scripts": {
    "android": "react-native run-android",
    "ios": "react-native run-ios",
    "start": "react-native start",
    "test": "jest",
    "lint": "eslint --ext .js,.jsx,.ts,.tsx ./"
    "lint:fix": "eslint --fix --ext .js,.jsx,.ts,.tsx ./"
  },
}
```

**`npm run lint`**

This command will run ESLint and display all the warnings and errors in your code.

**`npm run lint:fix`**

This command will run ESLint, display all the warnings and errors and it will even fix the issues if they are fixable by ESLint.

If the error messages are still shown up, open the source code and modify it to fix it!

# VSCode plugin setup

If you use VSCode, Use ESLint Extension to have the eslint information real-time in you VSCode Editor and when you save files, files are automatically fixed by ESLint rules like you execute `npm run lint:fix`

<img width="502" alt="ESlint-Extension" src="assets/ESLint.png">



Once you install the ESLint extention, this plugin needs a bit further configuration. Open the VSCode settings and add the following configuration.

```sh
"eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
]
```

# Done

That’s it. You can now write your code in React-native.
