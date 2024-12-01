# React help with issue and how to

## Official hosting help docs

<https://create-react-app.dev/docs/deployment/#serving-apps-with-client-side-routing>

## Issue fixing

### 1. Babel error

    One of your dependencies, babel-preset-react-app, is importing the
    "@babel/plugin-proposal-private-property-in-object" package without
    declaring it in its dependencies. This is currently working because
    "@babel/plugin-proposal-private-property-in-object" is already in your
    node_modules folder for unrelated reasons, but it may break at any time.

    babel-preset-react-app is part of the create-react-app project, which
    is not maintained anymore. It is thus unlikely that this bug will
    ever be fixed. Add "@babel/plugin-proposal-private-property-in-object" to
    your devDependencies to work around this error. This will make this message
    go away.

Install dependency: `npm install --save-dev @babel/plugin-proposal-private-property-in-object`

### 2. How to change port of react app

#### With "package.json" file

```text
  "scripts": {
    from -> "start": "react-scripts start", // default 3000
    to -> "start": "PORT=3006 react-scripts start", // set to 3006
  }
```

#### With `src/index.js`

From -> ReactDOM.render(<App />, document.getElementById('root'));
To -> ReactDOM.render(<App />, document.getElementById('root'), 3006);

#### Define `.env` file: This keeps the port config separate

PORT=3006
And access it via `process.env.PORT` in code, OR with some other way

## How to use .env in React

1. Way 1 (not recommended)

install 'npm i react-dotenv' and change the package.json "scripts" json to:
"scripts": {
"start": "react-dotenv && react-scripts start",
"build": "react-dotenv && react-scripts build",
"test": "react-dotenv && react-scripts test",
"serve": "react-dotenv && serve build",
"eject": "react-scripts eject"
}
add this
"react-dotenv": {
"whitelist": [
"KEY_Names1",
"KEY_Names2",
]
}
issue with this approach: it gives all the key to user visible in network tab and in window.

2. Way 2 (recommended)

Create a .env file in the root directory of project
Add custom variables with the prefix 'REACT*APP*', example: REACT_APP_API_KEY=123456789
Use 'process.env.REACT_APP_API_KEY' to access, example: const apiKey = process.env.REACT_APP_API_KEY;
Safe, no data leak

## Use SCSS

`npm install sass` and done

## Migrate a React Project to TypeScript (bad idea)

1. Install TypeScript and Type Definitions

npm install --save-dev typescript @types/node @types/react @types/react-dom @types/jest

1. Create a tsconfig.json File
