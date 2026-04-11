# the-react

A lightweight React-like library for **TheBugs Project**, written from scratch in TypeScript.

It provides a custom JSX runtime, component model, hooks, and routing primitives so you can build UI without using React itself.

## Features

- Custom JSX runtime.
- `createApp` entry point for mounting apps.
- Hooks like `useState` and `useEffect`.
- Router support with path matching and query parsing.
- TypeScript-first API.
- Designed to be used as an npm package.

## Installation

```bash
npm install the-react
```

## Setup

### `tsconfig.json`

Use the custom JSX source:

```json
{
  "compilerOptions": {
    "jsx": "react-jsx",
    "jsxImportSource": "the-react"
  }
}
```

### Example Vite usage

```ts
import { defineConfig } from 'vite';
import tsconfigPaths from 'vite-tsconfig-paths';

export default defineConfig({
  plugins: [tsconfigPaths()]
});
```

## Basic usage

```tsx
import { createApp, useState } from "the-react";

function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>Hello from the-react</h1>
      <button onClick={() => setCount(count + 1)}>
        Count: {count}
      </button>
    </div>
  );
}

const root = document.getElementById("app") as Element;
createApp(root, App);
```

## JSX runtime

This library ships its own JSX runtime, so JSX is transformed into calls that target `the-react` instead of React.

That means:

- no `React` import required,
- no dependency on React itself,
- your components are rendered by your own engine.

## Hooks

### `useState`

Stores component state and triggers updates when the value changes.

```tsx
const [value, setValue] = useState("");
```

### `useEffect`

Runs side effects when dependencies change or when the component mounts.

```tsx
useEffect(() => {
  console.log("mounted");
}, []);
```

## Project structure

```bash
the-react/
├── src/
│   ├── hooks/
│   ├── jsx-runtime/
│   ├── jsx-dev-runtime/
│   ├── my-react/
│   ├── types/
│   └── index.ts
├── package.json
├── tsconfig.json
└── README.md
```

## Build

```bash
npm run build
```

This produces the distributable package for use in other projects.

## Why this project exists

This library was created as part of **TheBugs Project** to explore how a frontend framework works under the hood:

- JSX transformation,
- rendering pipeline,
- state updates,
- effects,
- routing,
- package publishing.

It is a learning and engineering project, not just a wrapper around React.

## Roadmap

- improve reconciliation,
- add more hooks,
- expand router capabilities,
- support better dev runtime,
- improve DX and typings,
- add examples and tests.

## License

ISC

***

If you want, I can next turn this into a more polished README with badges, screenshots, API sections, and a nicer “Getting Started” flow.
