# vanilla-parceljs-gh-pages-deploy-test
Repository created to test deploy of a vanilla HTML/CSS/Javascript app bundled with ParcelJs on GitHub Pages

## Install Parcel globally

```
yarn global add parcel-bundler
```

## Create you html, css and js files, and add your images

Use a `./src` folder. Create your files in any order, indeed.

## Init `yarn` on app root

```
yarn init -y
```

## Run with Parcel

```
parcel src/index.html
```

## Build with Parcel

```
parcel build src/index.html
```

It will create a `dist` folder, with the bundle.

## Create a `.gitignore` for both `dist` and `node_modules`

```
dist/
node_modules/
.cache/
```

## Create Yarn tasks on `package.json`

```json
  "scripts": {
    "dev": "parcel src/index.html",
    "build": "parcel build src/index.html --public-url /<repo-name>/",
  }
```



## Install `gh-pages` as a dev-dependency
Do it on the app folder, not in root.

```
yarn add gh-pages -D
```

## Edit `package.json`

Add this (with you user and repo names):

```json
  "homepage": "http://<username>.github.io/<repo-name>",
```

And this:

```json
//...
"scripts": {
  //...
  "predeploy": "yarn build",
  "deploy": "gh-pages -d dist"
  //...
}
//...
```

## Run local with Yarn

```
yarn dev
```

## Deploy with Yarn

Run:

```
yarn deploy
```

It will build your app on `dist` folder and save it all on a branch named `gh-pages`. It will also commit, push and configure GitHub Pages!

Your source code is independent. Commit it at will. Your page will be updated only after a deploy.

## Enjoy!

This repository was created with this procedure. See it [live](http://ermogenes.github.io/vanilla-parceljs-gh-pages-deploy-test).