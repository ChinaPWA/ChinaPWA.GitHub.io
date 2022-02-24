---
title: "PWA Kit —— Consultative PWA toolset"
permalink: /en/cli/
lang: en-US
---

# PWA Kit —— Consultative PWA toolset

[![npm](https://img.shields.io/npm/v/@dingos/pwa-kit-cli)](https://www.npmjs.com/package/@dingos/pwa-kit-cli)
![NPM](https://img.shields.io/npm/l/@dingos/pwa-kit-cli)
![npm](https://img.shields.io/npm/dt/@dingos/pwa-kit-cli)
![node-current](https://img.shields.io/badge/node-%3E=14.0.0-green)

<div align=center>
<img src="https://chinapwa.github.io/assets/images/icon.png" style="zoom: 40%">
</div>

PWA Kit is a clever set of tools for [`Progressive Web Apps(PWA)`](https://web.dev/what-are-pwas/).
PWA Kit CLI is the CLI tool of PWA Kit.
## Features
- Consultative command interaction: Combine `one-off` and `Q&A` interaction modes, automatically ask for missing required items.
- Multiple Entries: Supports multiple operation entries such as folders, offline packages, and online URLs.
- Controllable and streamlined PWA generation.
- Automated code injection: One-click generation of various service worker templates and missing code.
- Preview Environment: Instantly visible preview of the effect.
- Multi-language, multi-framework scaffolding: A project creation method that supports TypeScript and common UI frameworks.

## Overview

The Web is an incredible platform. PWAs are designed to be powerful, reliable, and installable web applications on this platform.

For PWA, see [Google's official description](https://web.dev/progressive-web-apps/). PWA Kit is working hard to make PWA generation more convenient and smart.

Any web page can be easily converted into a PWA, and it also includes the basic elements such as manifest and Service Worker required for PWA. The PWA Kit also provides detection tools, through a standardized review score (Powered by Lighthouse), to indicate what is still missing and what needs to be done to convert a web page to a PWA. At the same time, PWA Kit can also intelligently fill in these missing contents.

## Preconditions

Installing `PWA Kit CLI` requires [`Node.js`](https://nodejs.org/en/download/releases/#ref-1) version higher than `14.0.0`, [`NPM`](https://www.npmjs.com/package/npm) version higher than `6.14.4`.


## Installation

The features provided by the `PWA Kit CLI` can be invoked from the command line using the **`kit`** command.

### Global Installation

```bash
npm install -g @dingos/pwa-kit-cli
```

### Local Installation

```bash
npm install @dingos/pwa-kit-cli
```

If the `PWA Kit CLI` is locally installed, and you want to use the `kit` command directly, you need to add the `.bin` subdirectory in the `node_modules` under the installation directory to the path of the environment variable.
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

The set of commands are as follows:

| command | description                              |
| ------ | ---------------------------------------   |
| gen    | Generate Service Worker, manifest         |
| inject | Inject Service Worker, manifest into HTML |
| create | Create a Vue.js or React based PWA project|
| upload | Upload the PWA to the preview environment |
| audit  | Audit the specified PWA                   |

Check out the `PWA Kit CLI` help manual:

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