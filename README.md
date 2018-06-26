# v-complete

> Autocomplete component using Vue 2 and Bootstrap

## Component Usage

In your project terminal:

```bash
npm i -s mykeels/v-complete
```

In your Vue script:

```js
import VueComplete from 'v-complete'

Vue.use('v-complete', VueComplete)
```

In your template html:

```html
<v-complete
  :suggestions="[
    { 'name': 'Bangladesh', 'description': 'Bangladesh' },
    { 'name': 'Lagos', 'description': 'Lagos' }
  ]"
  :limit="5"
  :threshold="0.3"
  value="Lagos"
  placeholder="Select a City"
  ></v-complete>
```

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
