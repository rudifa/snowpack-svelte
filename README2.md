# Snowpack + Svelte

A quick start [tutorial](https://www.webtips.dev/what-is-snowpack) by [webtips](https://www.webtips.dev/).

Create a Snowpack project

```
npx create-snowpack-app snowpack-svelte --template @snowpack/app-template-minimal
```

Install Svelte

```
npm i svelte @snowpack/plugin-svelte
```

Add the plugin to `snowpack.config.mjs` 

```
plugins: [
    '@snowpack/plugin-svelte'
],
```
Add `src/App.svelte`

Import and use `App` in `index.js`

At this stage the project has a rather flat file structure:

```
snowpack-svelte % tree-inm                                                           [:19da92a L|✔]
.
├── README.md
├── index.css
├── index.html
├── index.js
├── package-lock.json
├── package.json
├── public
├── snowpack.config.mjs
└── src
    └── App.svelte
```
The first `npm run build` adds the `build` folder which is the root of the web site.

Directly under `build` are files from the project root folder, processed or not, as required.

Even `package.json` and `snowpack.config.mjs` are there, which is unnecessary.

Under `build/_snowpack` are the dependency files processed by snowpack.

```
snowpack-svelte % tree-inm                                                           [:19da92a L|✔]
.
├── README.md
├── build
│   ├── README.md
│   ├── _snowpack
│   │   └── pkg
│   │       ├── import-map.json
│   │       └── svelte
│   │           └── internal.js
│   ├── index.css
│   ├── index.html
│   ├── index.js
│   ├── package-lock.json
│   ├── package.json
│   ├── snowpack.config.js
│   └── src
│       ├── App.svelte.css
│       ├── App.svelte.css.proxy.js
│       └── App.svelte.js
├── index.css
├── index.html
├── index.js
├── package-lock.json
├── package.json
├── public
├── snowpack.config.mjs
└── src
    └── App.svelte
```

To improve this, we add a mount configuraation to `snowpack.config.mjs`:

```
mount: {
    public: '/',
    src: '/dist'
},
```
Above specification means

- files under `public` shall go into the web site root (which is `build`)
- files under `src` shall go into the folder `dist` under the site root (`build/dist`)

Now we must move files and update the files access paths in files, to match the mount specification.

We also add an image as `public/assets/svelte.png` and reference it in the `App`.

```
snowpack-svelte % tree-inm                                                              [main L|✚1]
.
├── README.md
├── README2.md
├── build
│   ├── _snowpack
│   │   └── pkg
│   │       ├── import-map.json
│   │       └── svelte
│   │           └── internal.js
│   ├── assets
│   │   └── svelte.png
│   ├── dist
│   │   ├── App.svelte.css
│   │   ├── App.svelte.css.proxy.js
│   │   ├── App.svelte.js
│   │   └── index.js
│   ├── index.css
│   └── index.html
├── package-lock.json
├── package.json
├── public -------------------------------^ build
│   ├── assets
│   │   └── svelte.png
│   ├── index.css
│   └── index.html
├── snowpack.config.mjs
└── src ----------------------------------^ build/dist
    ├── App.svelte
    └── index.js
```



