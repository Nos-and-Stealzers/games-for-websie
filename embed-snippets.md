# Embed Snippets

You can mount each game directly into a page element with ES modules.

## 1) Add a mount target

```html
<div id="game-slot" style="width:100%;max-width:980px;margin:0 auto;"></div>
```

## 2) Import and mount one game

```html
<script type="module">
	import { mountMazeRunner } from '/embeds/maze-runner.js';

	const host = document.getElementById('game-slot');
	mountMazeRunner(host);
</script>
```

## 3) Game module paths

- `/embeds/maze-runner.js`
- `/embeds/arena-drift.js`
- `/embeds/cave-hopper.js`
- `/embeds/garden-defense.js`
- `/embeds/factory-freight.js`
- `/embeds/shipyard-scramble.js`

You can also import from a single barrel file:

```js
import {
	mountMazeRunner,
	mountArenaDrift,
	mountCaveHopper,
	mountGardenDefense,
	mountFactoryFreight,
	mountShipyardScramble
} from '/embeds/index.js';
```

## 4) Mount one host with a game selector

```html
<label for="game-select">Choose game:</label>
<select id="game-select"></select>
<div id="game-slot" style="width:100%;max-width:980px;margin:12px auto 0;"></div>

<script type="module">
	import { createGameSelector } from '/embeds/index.js';

	const host = document.getElementById('game-slot');
	const select = document.getElementById('game-select');

	createGameSelector(host, select, 'maze-runner');
</script>
```

## 5) Use styled game tabs (button switcher)

```html
<div id="game-tabs"></div>
<div id="game-slot" style="width:100%;max-width:980px;margin:12px auto 0;"></div>

<script type="module">
	import { createStyledGameTabs } from '/embeds/index.js';

	const host = document.getElementById('game-slot');
	const controls = document.getElementById('game-tabs');

	createStyledGameTabs(host, controls, 'maze-runner', {
		preset: 'sunset',
		background: '#fff7ed',
		textColor: '#7c2d12',
		hoverBackground: '#ffedd5',
		activeBackground: '#9a3412',
		activeTextColor: '#ffffff',
		borderColor: '#fed7aa',
		hoverBorderColor: '#fb923c',
		activeBorderColor: '#9a3412',
		borderRadius: '12px'
	});
</script>
```

Available presets:

- `default`
- `ocean`
- `sunset`
- `retro`

Preset-only example:

```js
import { createStyledGameTabs } from '/embeds/index.js';

createStyledGameTabs(host, controls, 'maze-runner', { preset: 'ocean' });
```

You can also inspect the preset map:

```js
import { gameTabThemePresets } from '/embeds/index.js';
console.log(gameTabThemePresets.retro);
```

Supported theme keys:

- `preset`
- `gap`
- `marginBottom`
- `fontFamily`
- `borderRadius`
- `borderColor`
- `background`
- `textColor`
- `hoverBackground`
- `hoverBorderColor`
- `activeBackground`
- `activeBorderColor`
- `activeTextColor`
- `padding`
- `fontSize`
- `fontWeight`
- `transition`

## Optional fallback

If you still prefer frame isolation, the original standalone HTML files are unchanged and can still be embedded with `iframe`.
