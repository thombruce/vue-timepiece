<h1 id="vue-timepiece" align="center">Vue Timepiece</h1>

<p align="center"><a href="https://www.patreon.com/thombruce"><img src="https://c5.patreon.com/external/logo/become_a_patron_button.png" alt="Become a Patron"></a></p>

<p align="center"><a href="https://github.com/thombruce/vue-timepiece/issues"><img src="https://img.shields.io/github/issues-raw/thombruce/vue-timepiece?logo=github" alt="GitHub issues"></a></p>

<p align="center"><a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License"></a></p>

<p align="center">Digital and analog clock component library for Vue.js.</p>

## Installation

```sh
# With Yarn
yarn add @thombruce/vue-timepiece
# With npm
npm install @thombruce/vue-timepiece --save
```

### If you're using Nuxt

Add `vue-timepiece/nuxt` to `buildModules` in `nuxt.config.js`:

```js
  buildModules: [
    // ...
    "@thombruce/vue-timepiece/nuxt",
    // ...
  ],
```

This will make all of Vue Timepiece's components available globally, so that you can use them without having to first `import` them.

## Usage

### Analog Clock

```vue
<template>
<timepiece-analog></timepiece-analog>
</template>
```

### Digital Clock

```vue
<template>
<timepiece-digital></timepiece-digital>
</template>
```

### Timer

```vue
<template>
<timepiece-timer :date='2000-01-01'></timepiece-timer>
</template>
```

### Countdown

```vue
<template>
<timepiece-countdown :date='2050-01-01'></timepiece-countdown>
</template>
```
