---
title: "PWA Kit —— 顾问式 PWA 工具集"
permalink: /zh/cli/
lang: zh-CN
---

# PWA Kit —— 顾问式 PWA 工具集

[![npm](https://img.shields.io/npm/v/@dingos/pwa-kit-cli)](https://www.npmjs.com/package/@dingos/pwa-kit-cli)
![NPM](https://img.shields.io/npm/l/@dingos/pwa-kit-cli)
![npm](https://img.shields.io/npm/dt/@dingos/pwa-kit-cli)
![node-current](https://img.shields.io/badge/node-%3E=14.0.0-green)

<div align=center>
<img src="https://chinapwa.github.io/assets/images/icon.png" style="zoom: 40%">
</div>

PWA Kit 是一套聪明的针对[“渐进式 Web 应用”(Progressive Web Apps 即 PWA)](https://web.dev/what-are-pwas/) 的工具集。
PWA Kit CLI 是 PWA Kit 针对命令行界面的版本。

## 特色

- 顾问式命令交互：融合一键式与问答式交互模式，自动询问缺失的必填项目。
- 多种入口：支持文件夹、离线包、在线 URL 等多种操作入口。
- 可控制的流程化 PWA 生成。
- 自动化代码注入：多种 service worker 模板与缺失的代码一键生成。
- 预览环境：即时可见的效果预览。
- 多语言、多框架脚手架：支持 TypeScript 及常见 UI 框架的项目创建方式。

## 概述

Web 是一个不可思议的平台。PWA 更是这个平台上经过设计的功能强大、可靠且可安装的 Web 应用程序。

关于 PWA，请参见 [Google 的官方描述](https://web.dev/progressive-web-apps/)。PWA Kit 正努力让 PWA 的生成更加便捷、智能。

任意的网页都可以轻松转换为 PWA，也包括了 PWA 所必需的 manifest、Service Worker 等基本要素。PWA Kit 也提供了检测工具，通过标准化的审查评分 (Powered by Lighthouse) 来提示网页转换为 PWA 还缺少什么，以及需要完成的内容。同时，PWA Kit 也可以智能化地来补全这些缺失的内容。

## 前置条件

安装 `PWA Kit CLI` 需要 [`Node.js`](https://nodejs.org/en/download/releases/#ref-1) 版本高于 `14.0.0`, [`NPM`](https://www.npmjs.com/package/npm) 版本高于 `6.14.4`。

## 安装

可以在命令行中使用 **`kit`** 命令来调用 `PWA Kit CLI` 提供的功能。

### 全局安装

```bash
npm install -g @dingos/pwa-kit-cli
```

### 局部安装

```bash
npm install @dingos/pwa-kit-cli
```

如果局部安装了 `PWA Kit CLI`，想直接使用 `kit` 命令，需要将安装目录下的 `node_modules` 中的 `.bin` 子目录添加到环境变量的 path 中。
或者，也可以安装 `npx`，然后在安装 `PWA Kit CLI` 的目录下运行 `npx kit <command>` 来使用局部安装的 `PWA Kit CLI`。

### 安装特定版本

例如：1.1.16 版本

```bash
npm install -g @dingos/pwa-kit-cli@1.1.16
```

## 使用说明

`PWA Kit CLI` 的命令组成如下所示：

```bash
kit <子命令> [ <参数> [可选参数] ]
```

子命令集合如下所示：

| 子命令 | 描述                                     |
| ------ | ---------------------------------------- |
| create | 创建一个基于 Vue.js 或 React 的 PWA 项目 |
| gen    | 生成 Service Worker, manifest            |
| inject | 将 Service Worker, manifest 注入到 HTML  |
| audit  | 检测指定的 PWA                           |

查看 `PWA Kit CLI` 使用手册：

```bash
kit --help
```

## 使用案例

### 创建一个 PWA 项目

我们可以用 `create` 命令来创建一个 `PWA` 项目

```bash
kit create <project_name>
```

其中 project_name 为创建项目的项目名称，接下来将通过 `问答式` 的方式补全其它选项，`问答式` 的选项列表如下所示
| 选项 | 描述 | 默认值 |
| --- | --- | --- |
PWA 的名称 | 用于指定 `manifest` 中的 `name` 字段 | Pwa Application |
PWA 的简短易读名称 | 用于指定 `manifest` 中的 `short_name` 字段 | PWA APP
PWA 启动时加载的 URL | 用于指定 `manifest` 中的 `start_url` | /index.html
PWA 的图标路径 (本地或网络地址) | 传入本地或者 web 图片地址，用于生成 `manifest` 中的 `icons` 字段，推荐使用 `512x512` 像素及其以上大小的图片 | <img src="/assets/images/icon.png" style="zoom:40%"> |
选择一个 `Service Worker` 模板 | 用于生成 `PWA` 的 `Service Worker` 模版，可选值包括：`OfflinePage`, `OfflineCopyOfPages`, `CacheFirstNetwork`, `AdvancedCaching`（关于 `Service Worker` 模板的具体含义请查看 `Service Worker` 模版介绍）| 无
选择 UI 框架 | 选择前端项目使用的 UI 框架，可选值包括 `vue`, `react` | 无
选择 Vue.js 版本 | 只有 UI 框架选择为 `vue` 时出现，可选择的值 `vue 2.x`, `vue 3.x` | 无
创建后自动安装 NPM 包 | 可选值 y/n | n

经过以上的`问答式`步骤后，我们将得到一个已添加 Manifest 和 Service Worker 配置的 PWA 项目

### 生成一个 Manifest 和 Service Worker 文件

我们可以用 `gen` 命令生成 Manifest 和 Service Worker 

```
kit gen
```

执行后可以通过 `问答式` 的方式补全其他选项，`问答式` 的选项列表如下所示
| 选项 | 描述 | 默认值 |
| --- | --- | --- |
选择您要生成的文件类型 | 用于指定生成的文件类型，可选值包括：Service Worker 和 Manifest, Service Worker, Manifest | 无

若选择的选项包含 Manifest，则会出现以下选项

| 选项 | 描述 | 默认值 |
| --- | --- | --- |
PWA 的名称 | 用于指定 `manifest` 中的 `name` 字段 | Pwa Application |
PWA 的简短易读名称 | 用于指定 `manifest` 中的 `short_name` 字段 | PWA APP
PWA 启动时加载的 URL | 用于指定 `manifest` 中的 `start_url` | /index.html
PWA 的图标路径 (本地或网络地址) | 传入本地或者 web 图片地址，用于生成 `manifest` 中的 `icons` 字段，推荐使用 `512x512` 像素及其以上大小的图片 | <img src="/assets/images/icon.png" style="zoom:40%"> |

若选择的选项包含 Service Worker，则会出现以下选项

| 选项 | 描述 | 默认值 |
| --- | --- | --- |
选择一个 `Service Worker` 模板 | 用于生成 `PWA` 的 `Service Worker` 模版，可选值包括：`OfflinePage`, `OfflineCopyOfPages`, `CacheFirstNetwork`, `AdvancedCaching`（关于 `Service Worker` 模板的具体含义请查看 `Service Worker` 模版介绍）| 无

执行后我们在当前路径下生成了 `Manifest` 和 `Service Worker` 

### 将 Manifest 和 Service Worker 注入到 html 中

我们可以用 `inject` 命令将 `Manifest` 和 `Service Worker` 注入到 `html` 中 

比如我们要将当前目录下的 `manifest.json` 注入到 html 中可以使用下面这种方式
 
```
kit inject index.html --manifest-path=./manifest.json
```

如果我们要将当前目录下的 `serviceWorker.js` 注入到 html 中可以使用下面这种方式

```
kit inject index.html --sw-path=./serviceWorker.js
```

### 使用 audit 命令

我们可以使用 `audit` 命令对 `PWA` 进行检测，命令如下所示

```
kit audit <url>
```

## 文档

`PWA Kit CLI` 英文文档：[文档链接](https://chinapwa.github.io/en/cli/)

`PWA Kit CLI` 详细使用文档：[文档链接](https://chinapwa.github.io/zh/cli/usage)

## 许可

[BSD-3-Clause](https://opensource.org/licenses/BSD-3-Clause)

## 其它

[pwa-kit-core](https://www.npmjs.com/package/@dingos/pwa-kit-core)  
[pwa-kit-template](https://www.npmjs.com/package/@dingos/pwa-kit-template)
