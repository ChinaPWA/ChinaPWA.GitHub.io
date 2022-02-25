---
title: "PWA Kit —— Consultative PWA toolset"
permalink: /en/cli/usage/
lang: en-US
---

# PWA Kit —— Consultative PWA toolset

## Usage

The command of `PWA Kit CLI` is as follows:

```bash
kit <command> [ <options> [optional options] ]
```

Supported commands are::

| command | description                                |
| :-----: | :----------------------------------------- |
|   gen   | Generate Service Worker, manifest          |
| inject  | Inject Service Worker, manifest into HTML  |
| create  | Create a Vue.js or React based PWA project |
| upload  | Upload the PWA to the preview environment  |
|  audit  | Detect Online PWAs                   |

Check out the `PWA Kit CLI` help manual:

```bash
kit --help
```

Commands in `PWA Kit CLI` support both `interactive` and `one-off` modes. When you are using `kit create <project_path> [options]` command to generate `PWA`, if none of the options are provided, `PWA Kit CLI` will promopt you for required items through `interactive promptings`, if some of the required `options` are filled in, then our `interactive prompting` interface will skip these provided options, and you only nedd to provide those unfilled options.

### gen

The command is as follows:

```bash
kit gen [options]
```

|    option    | required | default | description                                                                                                                  |
| :----------: | :------: | :-----: | :--------------------------------------------------------------------------------------------------------------------------- |
| `-o, --out`  |   yes    |   ./    | The path of generate file                                                                                                    |
| `-t, --type` |   yes    |   none    | Choose to generate `Service Worker`, `manifest`, or both, optional values ​​include &lt;all \| manifest \| serviceWorker&gt; |

#### manifest options

|        option         | required |                       default                        | description                                                                                                 |
| :-------------------: | :------: | :--------------------------------------------------: | :---------------------------------------------------------------------------------------------------------- |
|     `-n, --name`      |   yes    |                   PWA Application                    | The `name` field of the `manifest`                                                                          |
|    `--short-name`     |   yes    |                       PWA APP                        | The `short_name` field of the `manifest`                                                                 |
|      `--display`      |    no    |                     `standalone`                     | The `display` field of the `manifest`                                                                      |
| `-start, --start-url` |    yes    |                     /index.html                      | The `start_url` field of the `manifest`                                                          |
|       `--image`       |    yes    | <img src="/assets/images/icon.png" style="zoom:40%"> | A local or web image address, which is used to generate the `icons` field of the `manifest`. It is recommended to use an image with a size of `512x512` pixels and above |
| `--background-color`  |    no    |                      `#FFFFFF`                       | The `background-color` field of the `manifest`                                                            |
|    `--theme-color`    |    no    |                      `#FFFFFF`                       | The `theme_color` of the `manifest`                                                                |
|    `--description`    |    no    |                  A pwa application                   | The `description` field of the `manifest`                                                                 |
|       `--scope`       |    no    |                          ''                          | The `scope` field of the `manifest`

### Service Worker templates

We currently don't support generating `Service Worker` through `options` arguments but you can be set them through `interactive promptings`. Currently, 4 templates are supported. The detailed introduction is as follows:

|       template name       | description                                                                                                                                                 |
| :------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
|    `OfflinePage`     | This templete supports jump to an offline page named `offline.html` (which need to be created manually) when the network is disconnected.                                                                      |
| `OfflineCopyOfPages` |  Each page your visitors viewed is cached that allows the visitor to reload any previously viewed page while offline and extends the offline capabilities of your app.                 |
| `CacheFirstNetwork`  | THis caches static resources using the `CacheFirst` strategy. When the cached resource does not exist, it will be obtained through the network                                    |
|  `AdvancedCaching`   | Use this service worker to improve the performance of your application and make it work offline. Advanced cache service workers allow you to configure files and routes to be cached in different ways (pre-cache, server-first, cache-first, etc.) |

### inject

The inject command can inject `Service Worker`, `manifest` into your HTML files, so that your application can be quickly converted into a `PWA`.
The command is as follows:

```bash
kit inject <html_path> [options]
```

|       option       | required | default | description                               |
| :---------------: | :----: | :----: | :----------------------------------- |
| &lt;html_path&gt; |   no   |   none   | The HTML path to be injected       |
| `--manifest-path` |   no   |   none   | The `manifest` path to be injected       |
|    `--sw-path`    |   no   |   none   | The `Service Worker` path to be injected |

### create

`kit create` is used to generate a `PWA` project. The arguments that can be set include `manifest` configuration items, `Service Worker` templates, and specified front-end frameworks, including `Vue 2`, `Vue 3`, ` React`, using `TypeScript` or not, etc.
The command is as follows:

```bash
kit create <project_path> [options]
```

|         option         |          required          | default |                                            description                                              |
| :------------------: | :----------------------: | :----: | :-------------------------------------------------------------------------------------------: |
| &lt;project_path&gt; |            yes            |   none   |                          The directory where the `PWA` project is generated, do not specify a non-empty directory                          |
|     `--template`     |            yes            |   none   |                The framework used by the front-end project, optional values ​​include &lt;vue \| react &gt;                 |
|   `--vue-version`    | yes（When template is vue） |   none   | It takes effect when `template` is `vue`. It is used to specify the version of the  Vue framework. Optional values ​​include &lt;`2` \| `3`&gt; |
|    `--typescript`    |            yes            |   none   |          Whether the project uses the `TypeScript` framework, optional values ​​include &lt;true \| false &gt;          |
|   `--installable`    |            yes            |   none   |       Whether the system automatically downloads the `npm` package that the project depends on. The optional values ​​include &lt;true \| false &gt;        |
|     `--web-url`      |            no            |   none   |     `manifest`, `Service Worker` can be obtained through a `PWA` site, the priority will be lower than the options above      |

**manifest options and Service Worker templates are the same as the gen command**

> Please note that the front-end application is generated using the frameworks you chosen. So to start the project using `Vue`, use `npm run serve` and for `React` use `npm start`.

### upload

The upload command upload the `PWA` application to the preview environment we created where you can view the result of your `PWA` online.It takes about 2 hours for us to generate the preview.

The command is as follows:

```bash
kit upload <project_path>
```

|         option         | required | default |                                        description                                        |
| :------------------: | :----: | :----: | :---------------------------------------------------------------------------------: |
| &lt;project_path&gt; |   yes  |   none   | Upload the local `PWA` to the path address of the preview environment, note that there should be a unique `index.html` file in this path |

### audit

`PWA Kit CLI` also integrates the detection ability of `lighthouse` for `PWA`, which can generate multi-directional detection reports.
The command is as follows:

```bash
kit audit <url> [options]
```

|    option     | required | default |                                            description                                                |
| :---------: | :----: | :----: | :--------------------------------------------------------------------------------------------------: |
| &lt;url&gt; |   yes   |   none   |                                      To detect the address link of the PWA app                                       |
| `-t --type` |   yes   |  text  | Choose the form of generated test reports. Return the test results directly or a page containing the test results. The optional values ​​include &lt;text\|web&gt; |

### One-off mode

If you want to integrate `PWA Kit Cli` into your own application, you can embed `PWA Kit Cli` imperative commands into your code (provided you have `PWA Kit Cli` installed globally) , here we take the `inject` command as an example, the code example is as follows:

```javascript
const execa = require("execa");

await execa(
  "kit",
  [
    "inject",
    "./index.html",
    "--manifest-path",
    "./manifest.json",
    "--sw-path",
    "./serviceWorker.js",
  ],
  { stdio: "inherit" }
);
```
