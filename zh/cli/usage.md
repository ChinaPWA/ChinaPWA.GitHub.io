---
title: "PWA Kit —— 顾问式 PWA 工具集"
permalink: /zh/cli/usage/
lang: zh-CN
---

# PWA Kit —— 顾问式 PWA 工具集

## 使用说明

`PWA Kit CLI` 的命令组成如下所示：

```bash
kit <子命令> [ <参数> [可选参数] ]
```

子命令集合如下所示：

| 子命令 | 描述                                    |
| :----: | :-------------------------------------- |
| create | 创建一个 Vue 或 React 的 PWA 项目       |
|  gen   | 用于生成 Service Worker, manifest       |
| inject | 将 Service Worker, manifest 注入到 HTML |
| audit  | 检测在线 PWA                            |

查看 `PWA Kit CLI` 使用手册：

```bash
kit --help
```

注意 `PWA Kit CLI` 中的命令支持 `问答式` 和 `指令式` 两种形式，比如以 `kit create <project_path> [options]` 生成 `PWA` 的命令为例，当不输入任何 `options` 时，系统会将必填项做成问答的形式，您可以通过选择或者输入的形式进行补全，当您将所有必填的 `options` 都体现在命令中时，就会以 `指令式` 的形式执行，如果有一部分的必填项 `options` 被填写，那么问答式命令将跳过已被填写的参数，只需要回答那些未被填写的参数。

### gen 命令

该命令可以描述为：

```bash
kit gen [options]
```

|     参数     | 必填项 | 默认值 | 描述                                                                                                      |
| :----------: | :----: | :----: | :-------------------------------------------------------------------------------------------------------- |
| `-o, --out`  |   是   |   ./   | 生成文件的输出路径                                                                                        |
| `-t, --type` |   是   |   否   | 选择生成 `Service Worker`、`Manifest` 或者全都生成，可选的值包括 &lt;all \| manifest \| serviceWorker&gt; |

#### manifest 相关参数
|       参数        | 必填项 | 默认值 | 描述                                 |
| :---------------: | :----: | :----: | :----------------------------------- |
|     `-n, --name`      |   是   |                   PWA Application                    | 用于指定 `manifest` 中的 `name` 字段                                                                        |
|    `--short-name`     |   是   |                       PWA APP                        | 用于指定 `manifest` 中的 `short_name` 字段                                                                  |
|      `--display`      |   否   |                     `standalone`                     | 用于指定 `manifest` 中的 `display` 字段                                                                     |
| `-start, --start-url` |   是   |                     /index.html                      | 用于指定 `manifest` 中的 `start_url`                                                                        |
|       `--image`       |   是   | <img src="/assets/images/icon.png" style="zoom:40%"> | 传入本地或者 web 图片地址，用于生成 `manifest` 中的 `icons` 字段，推荐使用 `512x512` 像素及其以上大小的图片 |
| `--background-color`  |   否   |                      `#FFFFFF`                       | 用于指定 `manifest` 中的 `background_color` 字段                                                            |
|    `--theme-color`    |   否   |                      `#FFFFFF`                       | 用于指定 `manifest` 中的 `theme_color` 字段                                                                 |
|    `--description`    |   否   |                  A pwa application                   | 用于指定 `manifest` 中的 `description` 字段                                                                 |
|       `--scope`       |   否   |                          ''                          | 用于指定 `manifest` 中的 `scope` 字段                                                                       |

### Service Worker 模版

生成 `Service Worker` 目前还不支持 `options` 参数的方式，可以通过 `问答式` 进行选择，目前支持 4 种模版，详细的介绍如下所示：

|       模版名称       | 描述                                                                                                                                                 |
| :------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
|    `OfflinePage`     | 该方案会在断网时跳转到一个名为 `offline.html`（该页面需要您手动创建）的离线页面                                                                      |
| `OfflineCopyOfPages` | 一种扩展应用离线功能的解决方案。当您的访问者查看它们时，每个页面的副本都存储在缓存中。这允许访问者在离线时加载任何以前查看过的页面                   |
| `CacheFirstNetwork`  | 对静态资源采用 `CacheFirst` 策略进行缓存，`CacheFirst` 是一种以缓存为优先的策略，当缓存资源不存在时将通过网络获取                                    |
|  `AdvancedCaching`   | 使用此 Service Worker 来提高应用程序的性能，并使其脱机工作。高级缓存服务工作者允许您配置以不同方式缓存的文件和路由（预缓存、服务器优先、缓存优先等） |

### inject 命令

inject 命令可以将 `Service Worker`, `manifest` 注入到您已经写好的 HTML 中，从而使您的应用可以快速转化成 `PWA`  
注入的命令可以描述为：

```bash
kit inject <html_path> [options]
```

|       参数        | 必填项 | 默认值 | 描述                                 |
| :---------------: | :----: | :----: | :----------------------------------- |
| &lt;html_path&gt; |   是   |   无   | 将被注入的 HTML 路径                 |
| `--manifest-path` |   否   |   无   | 将要注入的 `manifest` 文件路径       |
|    `--sw-path`    |   否   |   无   | 将要注入的 `Service Worker` 文件路径 |

### create 命令

`kit create` 用于生成一个 `PWA` 项目，其可以设定的参数包括 `manifest` 的配置项，`Service Worker` 模版，指定的前端框架，包括 `Vue 2`，`Vue 3`，`React`，是否使用 `TypeScript` 等。  
创建 `PWA` 的命令可以描述为：

```bash
kit create <project_path> [options]
```

|         参数         |          必填项          | 默认值 |                                             描述                                              |
| :------------------: | :----------------------: | :----: | :-------------------------------------------------------------------------------------------: |
| &lt;project_path&gt; |            是            |   无   |                          生成 `PWA` 项目的目录，不要指定一个非空目录                          |
|     `--template`     |            是            |   无   |                用于指定前端项目使用的框架，可选的值包括 &lt;vue \| react &gt;                 |
|   `--vue-version`    | 是（template 为 Vue 时） |   无   | 当 `template` 指定为 `vue` 时生效，用于指定生成 Vue 框架的版本，可选值包括 &lt;`2` \| `3`&gt; |
|    `--typescript`    |            是            |   无   |          用于指定项目是否使用 `TypeScript` 框架，可选的值包括 &lt;true \| false &gt;          |
|   `--installable`    |            是            |   无   |       用于指定系统是否自动下载项目依赖的 `npm` 包，可选的值包括 &lt;true \| false &gt;        |
|     `--web-url`      |            否            |   无   |     可以通过一个 `PWA` 站点获取 `manifest`，`Service Worker`，优先级会低于上面配置的参数      |

**manifest 参数 和 Service Worker 模版同 gen 命令**

> 需要注意的是，前端应用底层使用各自框架的脚手架生成，所以在 `Vue` 下启动项目为 `npm run serve`，在 `React` 下启动为 `npm start`。

### audit 命令

`PWA Kit CLI` 也集成了 `lighthouse` 对 `PWA` 的检测功能，可以生成多维度的检测报告。  
检测 PWA 的命令可以描述为：

```bash
kit audit <url> [options]
```

|    参数     | 必填项 | 默认值 |                                                 描述                                                 |
| :---------: | :----: | :----: | :--------------------------------------------------------------------------------------------------: |
| &lt;url&gt; |   是   |   无   |                                        要检测 PWA 的地址链接                                         |
| `-t --type` |   是   |  text  | 生成检测报告的形式，支持直接返回检测结果或返回一个包含检测结果的页面，可选的值包括 &lt;text\|web&gt; |

### 指令式命令

如果想在您自己的应用程序中集成 `PWA Kit CLI`，您就可以将 `PWA Kit CLI` 的指令式命令内嵌到您的代码中（前提是您已经全局安装了 `PWA Kit CLI`），这里我们以 `inject` 命令为例，代码示例如下所示：

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
