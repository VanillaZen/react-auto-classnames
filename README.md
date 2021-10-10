# react-auto-classnames

Using `className={array|obj}` without `import 'classnames|clsx'`.

NOT a babel plugin.

## Installation

```
npm i react-auto-classnames
```

## Usage

If you use TypeScript, edit your `tsconfig.json` as:

```js
{
  "compilerOptions": {
    "jsx": "react-jsx",
    "jsxImportSource": "react-auto-classnames",
  }
}
```

If you use `@babel/preset-react` to transform jsx:

```js
// .babelrc / babel.config.json
{
  "presets": [
    "@babel/preset-typescript",
    [
      "@babel/preset-react",
      {
        "runtime": "automatic",
        "importSource": "react-auto-classnames"
      }
    ]
  ]
}

```

If you use esbuild (take *vite* for example):

```js
{
  esbuild: {
    jsxFactory: 'createElement',
    jsxFragment: 'Fragment',
    jsxInject: 'import { createElement, Fragment } from \'react-auto-classnames\'',
  },
}
```

Then you can write React code like this:

```js
function App() {
  return (
    <div className={['class-a', 'class-b', {
      'class-disabled': disabled,
    }]}>
  )
}

[clsx](https://github.com/lukeed/clsx) will be used to handle the `className` object.
```
