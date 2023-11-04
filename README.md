# TrileroVue

Basado en: 

https://github.com/raykotab/elTrileroGame

Game: El Trilero De Las Ramblas

    El Trilero ("shell-game" artist, or "Thimble-rig") is a typical Scam in las Ramblas de Barcelona for every tourist to enjoy... but sadly not anymore.

    The changes in social environments due to COVID-19 issues, have put a end to this traditional practice of subsidiary cosmic justice. It is in the interest of tourists as well as of scam-artists not to risk their Health.

    This application is intended to give visitors a grasp of the experience of being ripped off by a 'trilero'.

    First of all, this is a watered-down version of this experience.

    An important part of the thrill is being surrounded by menacing men playing their role, and the effort of the artists is to build up momentum on your nerves. And this, as the reader can most definetly understand, is not so easy to replicate on a web page app.

    E.g. Think an all those buttons who scream: "CLICK ME!!" all over the Internet, and you will see the Web is no stranger to this Philosophy

## PROPOSITO

Se trata de montar las diferentes animaciones, que sean responsive y desatrrollar la lógica del juego en 2 vertientes; una de juego de azar con resultados de bate y otra con usuario en la cual éste siempre perderá.

Ver Notas.md delproyecto en el link; para ver el proyecto chutando, instalarlo, instalar node_modules y npm run dev
 

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) to make the TypeScript language service aware of `.vue` types.

If the standalone TypeScript plugin doesn't feel fast enough to you, Volar has also implemented a [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) that is more performant. You can enable it by the following steps:

1. Disable the built-in TypeScript Extension
    1) Run `Extensions: Show Built-in Extensions` from VSCode's command palette
    2) Find `TypeScript and JavaScript Language Features`, right click and select `Disable (Workspace)`
2. Reload the VSCode window by running `Developer: Reload Window` from the command palette.

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Run End-to-End Tests with [Cypress](https://www.cypress.io/)

```sh
npm run test:e2e:dev
```

This runs the end-to-end tests against the Vite development server.
It is much faster than the production build.

But it's still recommended to test the production build with `test:e2e` before deploying (e.g. in CI environments):

```sh
npm run build
npm run test:e2e
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
