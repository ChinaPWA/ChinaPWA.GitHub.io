---
title: "PWA Kit —— Consultative PWA toolset"
permalink: /en/cli/
lang: en-US
---

# PWA Kit —— A consultative PWA toolset

[![npm](https://img.shields.io/npm/v/@dingos/pwa-kit-cli)](https://www.npmjs.com/package/@dingos/pwa-kit-cli)
![NPM](https://img.shields.io/npm/l/@dingos/pwa-kit-cli)
![npm](https://img.shields.io/npm/dt/@dingos/pwa-kit-cli)
![node-current](https://img.shields.io/badge/node-%3E=14.0.0-green)

<div align=center>
<img src="https://chinapwa.github.io/assets/images/icon.png" style="zoom: 40%">
</div>

PWA Kit is a smart toolset for [`Progressive Web Apps(PWA)`](https://web.dev/what-are-pwas/).
PWA Kit CLI enable you to use PWA Kit in your terminal.
## Features
- Consultative command: Combine `one-click` and `interactive` style interface to automatically ask for missing required options.
- Multiple Usages: Supports building pwa from local files, offline packages, and online URLs.
- User-defined pipelined PWA generations.
- Automated code injection: One-click to generate various service worker templates and complete missing components.
- Integrated preview Environment: Display the results instantly.
- Multi-language and multi-framework scaffolding: Supports TypeScript and most popular UI frameworks.

## Overview

PWAs as a incredible member of the amazing web world are designed to be powerful, reliable, and installable web applications.

If you want to know more about PWA, please see [Google's official description](https://web.dev/progressive-web-apps/). PWA Kit is built to make PWA generation more convenient and smart.

Any web page can be easily converted into a PWA if it has the basic elements such as manifest and Service Worker. The PWA Kit also provides  detection tools to give your site a standardized review score (Powered by Lighthouse), and find what is still missing and what needs to be done to convert a web page into a PWA. At the same time, PWA Kit can also smartly generate these missing contents.

## Prererequisite

Installing `PWA Kit CLI` requires [`Node.js`](https://nodejs.org/en/download/releases/#ref-1) version `14.0.0` and above and [`NPM`](https://www.npmjs.com/package/npm) version higher than`6.14.4`.


## Installation

### Global Installation

```bash
npm install -g @dingos/pwa-kit-cli
```

### Local Installation

```bash
npm install @dingos/pwa-kit-cli
```

Use the **`kit`** command to invoke `PWA Kit CLI`

If the `PWA Kit CLI` is locally installed and you want to use the `kit` command directly, you need to add the `.bin` subdirectory in the `node_modules` under the installed directory to the path of the environment variable.
Alternatively, you can install `npx`, then run `npx kit <command>` in the directory where the `PWA Kit CLI` is installed to use the locally installed `PWA Kit CLI`.

### Install a specific version

Example: Version 1.1.16

```bash
npm install -g @dingos/pwa-kit-cli@1.1.16
```

## Usage

The command of `PWA Kit CLI` is as follows:

```bash
kit <command> [ <options> [optional options] ]
```

Supported commands are:

| command | description                              |
| ------ | ---------------------------------------   |
| gen    | Generate Service Worker, manifest         |
| inject | Inject Service Worker, manifest into HTML |
| create | Create a Vue.js or React based PWA project|
| upload | Upload the PWA to the preview environment |
| audit  | Detect Online PWAs                        |

To check the `PWA Kit CLI` help manual:

```bash
kit --help
```

## Documentation

`PWA Kit CLI` detailed documentation: [link](https://chinapwa.github.io/en/cli/usage)

## Licenses

[BSD-3-Clause](https://opensource.org/licenses/BSD-3-Clause)

## Relationships Project

[pwa-kit-core](https://www.npmjs.com/package/@dingos/pwa-kit-core)  
[pwa-kit-template](https://www.npmjs.com/package/@dingos/pwa-kit-template)
