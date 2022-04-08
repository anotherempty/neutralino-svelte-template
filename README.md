# Neutralino + Svelte

<img src="https://i.ibb.co/xS6mJTY/image-2022-04-08-094444991.png" alt="Preview" style="max-width:800px">

There are many ways to integrate Svelte with Neutralino, this template shows one of them

## Table of contents

  - [How to use this template](#how-to-use-this-template)
  - [Manually integrate Svelte with Neutralino](#manually-integrate-svelte-with-neutralino)
  - [Running and Building](#running-and-building)
    - [Running in dev mode](#running-in-dev-mode)
    - [Building](#building)
  - [Using TypeScript](#using-typescript)
  - [Icon credits](#icon-credits)

<br>

## How to use this template

<ol>
  <li>
    <p>Create a Neutralino app using this template by running:</p>

```sh
npx degit anotherempty/neutralino-svelte-template your-app
```
  </li>
  <li>
    <p>Open your app base folder and initialize the Neutralino binaries:</p>

```sh
neu update
```
  </li>
  <li>
    <p>Go inside the <code>svelte</code> folder and install its dependencies:</p>

```sh
npm install
```
  </li>
  <li>
    <p>Finally run in dev mode or build your app, see the <a href="#running-and-building">Running and Building</a>
     section on how to.</p>
  </li>
</ol>

## Manually integrate Svelte with Neutralino

<ol>
  <li>
    <p>Create a Neutralino project with</p>

```sh
neu create
```

  </li>
  <li>
    <p>Open the Neutralino base folder and add Svelte:</p>

```sh
npx degit sveltejs/template svelte
```

  </li>
  <li>
    <p>(Optional) Delete the <code>README.md</code> from the svelte folder</p>
  </li>
  <li>
    <p>Copy the content of the Svelte <code>.gitignore</code> file inside the Neutralino <code>.gitignore</code> file then delete the Svelte <code>.gitignore</code> file</p>
  </li>
  <li>
    <p>Copy the <code>resources/js/neutralino.js</code> file to <code>svelte/public/</code></p>
  </li>
  <li>
    <p>Import the <code>neutralino.js</code> file inside <code>svelte/public/index.html</code>:</p>

```html
<script defer src="./build/bundle.js"></script>
<script src="./neutralino.js"></script>
```

  </li>
  <li>
    <p>Copy the <code>resources/icons/trayIcon.png</code> file to <code>svelte/public/</code></p>
  </li>
  <li>
    <p>(Optional) Copy the contents of <code>resources/js/main.js</code> inside the script tag of <code>svelte/src/App.svelte</code> and change the <code>trayIcon.png</code> path inside the <b>setTray()</b> function.</p>
    <p>Then copy the contents of the body of <code>resources/index.html</code> inside <code>svelte/src/App.svelte</code></p>
  </li>
  <li>
    <p>Open <code>neutralino.config.json</code> and change <b>documentRoot</b>, <b>modes.window.icon</b>, <b>modes.cloud.url</b> (optional if you're building a window app), <b>cli.resourcesPath</b>, and <b>cli.clientLibrary</b>:</p>

```json
{
  ...
  "documentRoot": "/svelte/public/",
  ...
  "modes": {
    "window": {
      "icon": "/svelte/public/favicon.png",
    }
    ...
    "cloud": {
      "url": "/svelte/public/#cloud",
    }
    ...
  }
  ...
  "cli": {
    "resourcesPath": "/svelte/public/",
    "clientLibrary": "/svelte/public/neutralino.js",
  }
}
```

  </li>
  <li>
    <p>Finally, delete the <code>resources</code> folder</p>
  </li>
</ol>

<br>

## Running and Building

### Running in dev mode

Open the <code>svelte</code> folder and install its dependencies ...

```bash
npm install
```

...then start [Rollup](https://rollupjs.org)...

```bash
npm run dev
```

...then open the base folder from another terminal and start Neutralino:

```bash
neu run
```

### Building 

Open the <code>svelte</code> folder and run the build command ...

```bash
npm run build
```

... then from the base folder, build the Neutralino app

```bash
neu build
```

## Using TypeScript

Go inside the <code>svelte</code> folder and run :

```bash
node scripts/setupTypeScript.js
```

## Icon credits

- `trayIcon.png` - Made by [Freepik](https://www.freepik.com) and downloaded from [Flaticon](https://www.flaticon.com)
