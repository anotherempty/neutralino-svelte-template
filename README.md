# Neutralino + Svelte

There are many ways to integrate Svelte with Neutralino, this template shows one of them

## Table of contents

  - [Integration](#integration)
  - [Get started](#get-started)
    - [Building and running in production mode](#building-and-running-in-production-mode)
    - [Using TypeScript](#using-typescript)
  - [Icon credits](#icon-credits)

<br>


## Integration

<ol>
  <li>
    <p>Create a Neutralino project:</p>

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

## Get started

Open the <code>svelte</code> folder and install the its dependencies ...

```bash
npm install
```

...then start [Rollup](https://rollupjs.org)...

```bash
npm run dev
```

...then start Neutralino in another terminal:

```bash
neu run
```

### Building and running in production mode

Open the <code>svelte</code> folder and run the build command ...

```bash
npm run build
```

... then go back to the base folder and build the Neutralino app

```bash
neu build
```

### Using TypeScript

Go inside the <code>svelte</code> folder and run :

```bash
node scripts/setupTypeScript.js
```

## Icon credits

- `trayIcon.png` - Made by [Freepik](https://www.freepik.com) and downloaded from [Flaticon](https://www.flaticon.com)
