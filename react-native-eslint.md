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

# Configure ESLint

Run the command below in project root folder to initialize ESLint to your workspace.

```sh
npx eslint --init
```

On Configuring the above command it will ask you a few questions via CLI. Here’s a list of them, and the answers we’ll need to choose (✔ and ❯ symbols indicate the selected answers):

<img width="723" alt="Configuration-1 Image" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/Config-1.png">

On selecting `To check syntax, find problems, and enforce code style ` it'll check style and fix it automatically.

<img width="719" alt="Configuration-2 Image" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/Config-2.png">

Select `JavaScript modules (import/export) ` to go next

<img width="721" alt="Configuration-3 Image" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/Config-3.png">

React Native is based on React, so select `React`.

<img width="722" alt="Configuration-4 Image" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/Config-4.png">

Choose your project configuration and procced, In this project I am using JavaScript, so I selected N to configure ESLint.

<img width="722" alt="Configuration-5 Image" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/Config-5.png">

React Native is not run on the browser, so select only `Node`.

<img width="914" alt="Configuration-6 Image" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/Config-6.png">

This question is what style you want to implement via ESLint. I selected `Use a popular style guide option ` to use some standard syles.

<img width="913" alt="Configuration-7 Image" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/Config-7.png">

Since the airbnb style guide are quite popular and reasonable, stick with them as much as possible we'll rely on Airbnb's JavaScript style guide here.

<img width="715" alt="Configuration-8 Image" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/Config-8.png">

This question is about what file you want to save ESLint settings. .eslintrc.js file exists already in React Native, so select `JavaScript` to overwrite it.

<img width="917" alt="Configuration-9 Image" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/Config-9.png">

In the final prompt ESLint will ask you to install all the necessary dependencies. Select "Yes" and hit enter.

As a result, you’ll end up having a .eslintrc.json file in the root of your project and install React Native specific rules

```sh
npm install --save-dev eslint-plugin-react-native
```

Open `.eslintrc.js` file and modify it like the below configuration.

```js
module.exports = {
  env: {
    browser: true,
    es2021: true,
    "react-native/react-native": true,
  },
  extends: ["plugin:react/recommended", "airbnb", "airbnb/hooks"],
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: "latest",
    sourceType: "module",
  },
  plugins: ["react", "react-native"],
  rules: {
    "react/jsx-filename-extension": [1, { extensions: [".js", ".jsx"] }],
  },
};
```

# Usage

Add below scripts in your package.json to run lint on all files including .js and .tsx ones and to fix them.

```sh
{
  ...
  "scripts": {
    ...
    "lint": "eslint --ext .js,.jsx,.ts,.tsx ./"
    "lint:fix": "eslint --fix --ext .js,.jsx,.ts,.tsx ./"
    ...
  },
  ...
}
```

**`npm run lint`**

This command will run ESLint and display all the warnings and errors in your code.

**`npm run lint:fix`**

This command will run ESLint, display all the warnings and errors and it will even fix the issues if they are fixable by ESLint.

If the error messages are still shown up, open the source code and modify it to fix it!

# VSCode plugin setup

If you use VSCode, Use ESLint Extension to have the eslint information real-time in you VSCode Editor and when you save files, files are automatically fixed by ESLint rules like you execute `npm run lint:fix`

<img width="502" alt="ESlint-Extension" src="https://raw.githubusercontent.com/RaviTejaKoduru/lint-docs/main/ESLint.png">

Once you install the ESLint extention, this plugin needs a bit further configuration. Open the VSCode settings and add the following configuration.

```sh
"eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
]
}
```

# Done

That’s it. You can now write your code in React-native.
