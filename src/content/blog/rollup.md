---
author: YgamiJS
pubDatetime: 2023-04-18
title: Сборщик модулей Rollup
postSlug: Сборщик модулей Rollup
featured: true
draft: false
tags:
  - rollup
ogImage: "https://github.githubassets.com/images/modules/profile/achievements/pull-shark-default.png"
description: Сборщик модулей Rollup
---

## Rollup - сборщик модулей JavaScript , мы быстро его осмотрим

> Скомпилируйте небольшие фрагменты кода в нечто большее и более сложное.

[Rollup.js](https://rollupjs.org/) достаточно популярный , на нем построен другой популярный сборщик [Vite.js](https://vitejs.dev/).

Rollup.js работает как в браузере так и на Node.js , он совместим с ES модулями и CommonJS. Vue , Angular , moment.js и другие популярные проекты используют Rollup.js

Он представляет собой сборщик модулей, который позволяет создавать бандлы, объединяющие модули приложения в единую статическую файловую структуру. Rollup.js был создан с учетом особенностей создания библиотек и позволяет оптимизировать код, удаляя неиспользуемый код и уменьшая размер файлов.

Начнем!

## Установка

### Глобальная установка

```bash
npm install --global rollup
```

### Локальная установка

```bash
npm install rollup --save-dev
```

Rollup.js можно использовать через [CLI](https://rollupjs.org/command-line-interface/) c необезательным файлом конфигурации или через его [JavaScript API](https://rollupjs.org/javascript-api/)

## Просмотр доступных опций и параметров

```bash
rollup --help
```

## Компиляция

### Для браузеров

```bash
rollup main.js --file bundle.js --format iife
```

### Для Node.js

```bash
# compile to a CommonJS module ('cjs')
rollup main.js --file bundle.js --format cjs
```

### Как для браузеров, так и для Node.js

```bash
# UMD format requires a bundle name
rollup main.js --file bundle.js --format umd --name "myBundle"
```

## Файл конфигурации

Файлы конфигурации свертывания являются необязательными, но они являются мощными и удобными и поэтому **рекомендуются**. Файл конфигурации — это модуль ES, который экспортирует объект по умолчанию с нужными параметрами

```js
export default {
  input: "src/main.js",
  output: {
    file: "bundle.js",
    format: "cjs",
  },
};
```

Чтобы использовать Rollup с файлом конфигурации, передайте `--config` или `-c` флаг

```bash
# pass a custom config file location to Rollup
rollup --config my.config.js

# if you do not pass a file name, Rollup will try to load
# configuration files in the following order:
# rollup.config.mjs -> rollup.config.cjs -> rollup.config.js
rollup --config
```

Чтобы наблюдать за измениями и пересобирать бандл установите опцию `-w` или `--watch`

Это был краткий обзор сборщика модулей Rollup.js , более подробно вы можете ознакомиться на его [сайте](https://rollupjs.org/)
