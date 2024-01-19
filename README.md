# .

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

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

### Compile and Minify for Production

```sh
npm run build
```
```bash

..# 1. Crea repo su git (senza opzioni se non pubblico)
# 2. Clonare la repo e apri la cartella su vs code e aprire terminale
# 3. digitare: npm create vue@latest
# 4. per creare il progetto nella directory corrente mettere solo un punto
# 5. nome package lo stesso della cartella poi lasciare tutto come sta
# 6. dire si all'opzione vue router
# 7. npm install
# 8. npm run dev

npm install bootstrap axios @fortawesome/fontawesome-free sass

# eventualmente facciamo vedere fontsource: https://fontsource.org/fonts/montserrat
npm install @fontsource/montserrat

# copiamo la cartella webfonts da @fortawesome in node-modules in assets
# crea la cartella style e dentro questa crea una partials
#  crea un file variables.scss dentro partials, questo file hosterà le variabili scss
# cambia il main.css a main.scss ed inseriscilo in style

# incolla in style i link alle variabili, fontawesome e bootstrap:
@use '/src/assets/partials/variables.scss' as *;

$fa-font-path: '../webfonts';
@import '@fortawesome/fontawesome-free/scss/fontawesome.scss';
@import '@fortawesome/fontawesome-free/scss/solid.scss';
@import '@fortawesome/fontawesome-free/scss/regular.scss';
@import '@fortawesome/fontawesome-free/scss/brands.scss';

@import 'bootstrap/scss/bootstrap';

# vai nel main.js e cambia l'importazione del file da main.css a main.scss

# elimina le componenti inutili come quella nella cartella components>icons, 
# i file vue Helloworld, thewelcome e welcomeItem

# crea una cartella data in assets, qua creeremo il file store.js
# che hosterà i dati da sharare tra le varie componenti
# incolla in store.js :
import {reactive} from "vue";

export const store = reactive({
    apiUrl:'http://127.0.0.1:8000/api'
});

# inizialmente commentiamo l'importazione e l'uso del router di view dal main js


npm run dev -- --port 5174 (API_URL='http://127.0.0.1:8000/api')

```