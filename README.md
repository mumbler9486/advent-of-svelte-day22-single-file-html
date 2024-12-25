# advent-of-svelte-day22-single-file-html

A demo project for the Advent of Svelte 2024 day 22. Made the fortune teller part using Claude Sonnet 3.5. Based on the project https://github.com/Rich-Harris/snek

[See my main solutions page ](https://github.com/mumbler9486/mumbler9486-advent-of-svelte-2024)

Configurations needed to export a single HTML file that can be runned off a "floppy disk"

* Set `build.assetsInlineLimit` to `Infinity` in `vite.config.ts`
* In `svelte.config.js` set:
  * `kit.router.type` to `'hash'` (likewise all links should be like `href="#/path"`
  * `kit.output.bundleStrategy` to `'inline'`
* Use the `@sveltejs/adapter-static` adapter
* For any asset files that are to be bundled together import them via the `lib` folder like `import myAsset from "$lib/path/to/my/asset.png"`
  * For sound files, create an Audio object on `onMount()` to be used later
  * For image files, you can refer to them in img tags using `src={myImage}`


## Building the Project

Build with

```SHELL
pnpm install
pnpm run build
```

Then you can find the resulting HTML file in `build/index.html` which you can run in a browser without a server.
