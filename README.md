# Introduction
ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code, with the goal of making code more consistent and avoiding bugs.

This repository will document different technology specific linting rules for ESLint.

At [Osmosys Software Solutions Pvt Ltd](https://osmosys.co/) we standardize the ESLint configuration, which will be used across multiple projects.

# What you will learn?

We will see how you can setup ESLint to an existing React app. This document will guide you through the ESLint setup process on a basic React app which is using typescript template.

# Prerequisite

- React app with typescript
Any existing React app with typescript. If you don't have one then you can create a basic React app using the following command.

```sh
npx create-react-app my-app --template typescript
```

- Node.js

[Node.js](https://nodejs.org/en/) (`^12.22.0`, `^14.17.0`, or `>=16.0.0`) built with SSL support. (If you are using an official Node.js distribution, SSL is always built in.)

# Installation

You can install ESLint using

```sh
npm install eslint --save-dev
```

> **Note**: for now assuming we will use `npm` over `yarn`

You should then set up a configuration file, and the easiest way to do that is:

```sh
npm init @eslint/config
```

> **Note**: `npm init @eslint/config` assumes you have a `package.json` file already. If you don't, make sure to run `npm init` beforehand.

```
Need to install the following packages:
  @eslint/create-config
Ok to proceed? (y)
```

Press `y` and hit `Enter`

```sh
? How would you like to use ESLint? …
  To check syntax only
  To check syntax and find problems
▸ To check syntax, find problems, and enforce code style
```

ESLint will then ask you how you want to use ESLint, here pick the last option which is `To check syntax, find problems, and enforce code style`.

```sh
? What type of modules does your project use? …
▸ JavaScript modules (import/export)
  CommonJS (require/exports)
  None of these
```

Now select the first option `JavaScript modules (import/export)`.

```sh
? Which framework does your project use? …
▸ React
  Vue.js
  None of these
```

Select `React` since this is a React application.

```sh
? Does your project use TypeScript? ‣ No / Yes
```

Select `Yes` here, since we are going to always use `TypeScript` for all projects.

```sh
? Where does your code run?
✔ Browser
  Node
```

Since the code will run on browser, please select `Browser`.

```sh
? How would you like to define a style for your project? …
▸ Use a popular style guide
  Answer questions about your style
```

Select `Use a popular style guide`.

```sh
? Which style guide do you want to follow? …
  Airbnb: https://github.com/airbnb/javascript
▸ Standard: https://github.com/standard/standard
  Google: https://github.com/google/eslint-config-google
  XO: https://github.com/xojs/eslint-config-xo
```

Select`Standard`guide for now.

```sh
? What format do you want your config file to be in? …
  JavaScript
  YAML
▸ JSON
```

Select `JSON` here sine that is the easiest one to read.

```sh
Checking peerDependencies of eslint-config-standard@latest
? The style guide "standard" requires eslint@^7.12.1. You are currently using eslint@8.11.0.
  Do you want to downgrade? ‣ No / Yes
```

You might encounter this error if you are using the most recent version of eslint. Since the `Standard` guide uses `eslint@^7.12.1`.

```sh
The config that you've selected requires the following dependencies:

eslint-plugin-react@latest @typescript-eslint/eslint-plugin@latest eslint-config-standard@latest eslint@^7.12.1 eslint-plugin-import@^2.22.1 eslint-plugin-node@^11.1.0 eslint-plugin-promise@^4.2.1 || ^5.0.0 @typescript-eslint/parser@latest
? Would you like to install them now with npm? ‣ No / Yes
```

You will see all the dependencies which are required and select `Yes` to install them.

# Usage

You then have to add couple of script commands to run ESLint.

```
"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "lint": "eslint src --ext .js,.jsx,.ts,.tsx --max-warnings=0",
    "lint-fix": "eslint src --ext .js,.jsx,.ts,.tsx --fix"
  },
```

**`npm run lint`**

This command will run ESLint and display all the warnings and errors in your code.

**`npm run lint-fix`**

This command will run ESLint, display all the warnings and errors and it will even fix the issues if they are fixable by ESLint.

# Additional steps

## Fix Warning

When you run `npm run lint` you might will see the following warning

```sh
Warning: React version not specified in eslint-plugin-react settings. See https://github.com/yannickcr/eslint-plugin-react#configuration .
```

Add the below object to your `.eslintrc.json` file, this will resolve the above warning.

```sh
"settings": {
    "react": {
      "version": "detect"
    }
},
```
