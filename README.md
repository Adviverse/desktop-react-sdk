# @adviverse/desktop-react

`<AdviverseAd/>` — a drop-in React ad card for desktop apps that host a webview
(Electron, Tauri, CEF). Built on [`@adviverse/desktop`](https://github.com/Adviverse/desktop-sdk):
fetch → render a disclosed card → impression on true viewability → click opens the
default browser. Renders nothing on no-fill.

## Install

```sh
npm install @adviverse/desktop-react
```

Get a **serve token** (`ts_…`) from your Adviverse dashboard (Publisher → Placements →
terminal/SDK token).

## Usage

```tsx
import { AdviverseAd } from '@adviverse/desktop-react';

// A disclosed ad card. Renders nothing on no-fill; rotates if you pass refreshMs.
<AdviverseAd token="ts_yourtoken" refreshMs={60000} /* min 30000; paused while hidden */ />
```

Bring your own markup with a render prop:

```tsx
<AdviverseAd token="ts_yourtoken">
  {(ad, onClick) => (
    <button onClick={onClick}>{ad.label} · {ad.text} {ad.cta && `— ${ad.cta}`}</button>
  )}
</AdviverseAd>
```

## Electron

In Electron, also install [`@adviverse/electron`](https://github.com/Adviverse/electron-sdk)
in the main process so clicks open the system browser instead of your app window.
Config options (consent, uid, base, …) are the same as `@adviverse/desktop`.
