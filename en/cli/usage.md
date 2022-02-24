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

The set of commands are as follows:

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

Note that the commands in `PWA Kit CLI` support both `Q&A` and `one-off` modes. For example, take the `kit create <project_path> [options]` command to generate `PWA`, when no options are entered, the system will make the required items in the form of `Q&A`, if some of the required `options` are filled in, then then `Q&A` will skip the filled options, and only need to answer those unfilled options.

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

Generating `Service Worker` currently does not support the `options` , which can be selected through `Q&A`. Currently, 4 templates are supported. The detailed introduction is as follows:

|       template name       | description                                                                                                                                                 |
| :------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
|    `OfflinePage`     | The solution will jump to an offline page named `offline.html` (this page needs to be created manually) when the network is disconnected                                                                      |
| `OfflineCopyOfPages` | A solution to extend the offline capabilities of your app. A copy of each page is stored in the cache as your visitors view them. This allows the visitor to load any previously viewed page while offline                  |
| `CacheFirstNetwork`  | Cache static resources using the `CacheFirst` strategy. When the cached resource does not exist, it will be obtained through the network                                    |
|  `AdvancedCaching`   | Use this service worker to improve the performance of your application and make it work offline. Advanced cache service workers allow you to configure files and routes to be cached in different ways (pre-cache, server-first, cache-first, etc.) |

### inject

The inject command can inject `Service Worker`, `manifest` into the HTML you have written, so that your application can be quickly converted into `PWA`.  
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

`kit create` is used to generate a `PWA` project. The parameters that can be set include `manifest` configuration items, `Service Worker` templates, and specified front-end frameworks, including `Vue 2`, `Vue 3`, ` React`, whether to use `TypeScript`, etc.
The command is as follows:

```bash
kit create <project_path> [options]
```

|         option         |          required          | default |                                            description                                              |
| :------------------: | :----------------------: | :----: | :-------------------------------------------------------------------------------------------: |
| &lt;project_path&gt; |            yes            |   none   |                          The directory where the `PWA` project is generated, do not specify a non-empty directory                          |
|     `--template`     |            yes            |   none   |                The framework used by the front-end project, optional values ​​include &lt;vue \| react &gt;                 |
|   `--vue-version`    | yes（When template is vue） |   none   | It takes effect when `template` is `vue`. It is used to specify the version of the generated Vue framework. Optional values ​​include &lt;`2` \| `3`&gt; |
|    `--typescript`    |            yes            |   none   |          Whether the project uses the `TypeScript` framework, optional values ​​include &lt;true \| false &gt;          |
|   `--installable`    |            yes            |   none   |       Whether the system automatically downloads the `npm` package that the project depends on. The optional values ​​include &lt;true \| false &gt;        |
|     `--web-url`      |            no            |   none   |     `manifest`, `Service Worker` can be obtained through a `PWA` site, the priority will be lower than the options above      |

**manifest options and Service Worker templates are the same as the gen command**

> It should be noted that the front-end application is generated using the scaffolding of the respective frameworks, so to start the project under `Vue` is `npm run serve`, and under `React` it is `npm start`.

### upload

The upload command can upload the `PWA` application to the preview environment we prepared, and check the effect of the `PWA` deployed online. The effective time to view the preview result is 2 hours after you upload the preview application.
The command is as follows:

```bash
kit upload <project_path>
```

|         option         | required | default |                                        description                                        |
| :------------------: | :----: | :----: | :---------------------------------------------------------------------------------: |
| &lt;project_path&gt; |   yes  |   none   | Upload the local `PWA` to the path address of the preview environment, note that there should be a unique `index.html` file in this path |

### audit

`PWA Kit CLI` also integrates the detection function of `lighthouse` for `PWA`, which can generate multi-dimensional detection reports.
The command is as follows:

```bash
kit audit <url> [options]
```

|    option     | required | default |                                            description                                                |
| :---------: | :----: | :----: | :--------------------------------------------------------------------------------------------------: |
| &lt;url&gt; |   yes   |   none   |                                      To detect the address link of the PWA app                                       |
| `-t --type` |   yes   |  text  | The form of generating a test report supports returning the test results directly or returning a page containing the test results. The optional values ​​include &lt;text\|web&gt; |

### One-off mode

If you want to integrate `PWA Kit Cli` in your own application, you can embed `PWA Kit Cli` imperative commands into your code (provided you have `PWA Kit Cli` installed globally) , here we take the `inject` command as an example, the code example is as follows:

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
