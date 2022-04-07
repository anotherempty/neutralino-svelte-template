<script>
  import { onMount } from "svelte";

	let info = "";

  const showInfo = () => {
    info = `
        ${NL_APPID} is running on <i>port ${NL_PORT}</i>  inside ${NL_OS}
        <br/><br/>
        <span>server: v${NL_VERSION} . client: v${NL_CVERSION}</span>
        `;
  };

  const openNeuDocs = () => {
    Neutralino.os.open("https://neutralino.js.org/docs");
  };

  const openNeuTutorial = () => {
    Neutralino.os.open(
      "https://www.youtube.com/watch?v=txDlNNsgSh8&list=PLvTbqpiPhQRb2xNQlwMs0uVV0IN8N-pKj"
    );
  };

  const openSvelteTuto = () => {
    Neutralino.os.open("https://svelte.dev/tutorial");
  };

  const setTray = () => {
    if (NL_MODE != "window") {
      console.log("INFO: Tray menu is only available in the window mode.");
      return;
    }
    let tray = {
      icon: "/svelte/public/trayIcon.png",
      menuItems: [
        { id: "VERSION", text: "Get version" },
        { id: "SEP", text: "-" },
        { id: "QUIT", text: "Quit" },
      ],
    };
    Neutralino.os.setTray(tray);
  };

  const onTrayMenuItemClicked = (event) => {
    switch (event.detail.id) {
      case "VERSION":
        Neutralino.os.showMessageBox(
          "Version information",
          `Neutralinojs server: v${NL_VERSION} | Neutralinojs client: v${NL_CVERSION}`
        );
        break;
      case "QUIT":
        Neutralino.app.exit();
        break;
    }
  };

  const onWindowClose = () => {
    Neutralino.app.exit();
  };

  Neutralino.events.on("trayMenuItemClicked", onTrayMenuItemClicked);
  Neutralino.events.on("windowClose", onWindowClose);

  if (NL_OS != "Darwin") {
    // TODO: Fix https://github.com/neutralinojs/neutralinojs/issues/615
    setTray();
  }

  onMount(() => {
    showInfo();
  });
</script>

<main>
  <h1>NeutralinoJs + Svelte</h1>
  <p>
    Visit the <a href="#" on:click={() => openSvelteTuto()}>Svelte tutorial</a> to
    learn how to build Svelte apps.
  </p>
  <div>{@html info}</div>
  <div>
    <a href="#" on:click={() => openNeuDocs()}>Neutralino Docs</a> &middot;
    <a href="#" on:click={() => openNeuTutorial()}>Neutralino Tutorial</a>
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
