---
title: "PWA Kit CLI"
permalink: /zh/
lang: zh-CN
---

# PWA Kit CLI

[![npm](https://img.shields.io/npm/v/@dingos/pwa-kit-cli)](https://www.npmjs.com/package/@dingos/pwa-kit-cli)
![NPM](https://img.shields.io/npm/l/@dingos/pwa-kit-cli)
![npm](https://img.shields.io/npm/dt/@dingos/pwa-kit-cli)
![node-current](https://img.shields.io/badge/node-%3E=14.0.0-green)
<div align=center>
<img src="https://cdn.jsdelivr.net/npm/@dingos/pwa-kit-cli/pwa-kit.png" style="zoom:40%">
</div>

## 概述

`PWA Kit CLI` 是一组实用工具集合，是 `PWA Kit` 项目的 CLI 分支。它可以将任意潜在的网站转换为 [**`PWA`**](https://web.dev/progressive-web-apps/) (Progressive Web Application，渐进式网络应用)，也包括了 PWA 所必须的 [清单 (manifest)](https://web.dev/add-manifest/) 和 [Service Worker](https://web.dev/learn/pwa/service-workers/) 等基本要素。
除此之外，`PWA Kit CLI` 也提供了 PWA 检测工具，通过标准化的审查评测机制分类评分来提示当前网站转换为 PWA 还缺少什么，以及需要完成的内容。不过我们并不需要为这些缺少的部分而担心，`PWA Kit CLI` 的使命正是智能化的来完成这些工作。

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

如果局部安装了 `PWA Kit CLI`，想直接使用 `kit` 命令，需要将安装目录下的 `node_modules` 中的 `.bin` 目录添加到环境变量的 path 中，或者，也可以安装 `npx`，然后在安装 `PWA Kit CLI` 的目录下运行 `npx kit <command>` 就可以使用局部安装的 `PWA Kit CLI`。

### 安装特定版本（例如：1.1.16 版本）

```bash
npm install -g @dingos/pwa-kit-cli@1.1.16
```

## 使用说明

`PWA Kit CLI` 的命令组成如下所示：  
```bash
kit <子命令> [ <参数> [可选参数] ]
```
子命令集合如下所示：

| 子命令 | 描述 |
|---|---|
| gen | 生成 Service Worker, manifest |
| inject | 将 Service Worker, manifest 注入到 HTML |
| create | 创建一个基于 Vue 或 React 的 PWA 项目 |
| upload | 上传 PWA 到预览环境 |
| audit  | 检测指定的 PWA |
 
 
查看 `PWA Kit CLI` 使用手册：
```bash
kit --help
```

## 文档

`PWA Kit CLI` 详细使用文档：[文档链接](https://chinapwa.github.io/usage)


## 许可

[BSD-3-Clause](https://opensource.org/licenses/BSD-3-Clause)

## 其它

[pwa-kit-core](https://www.npmjs.com/package/@dingos/pwa-kit-core)  
[pwa-kit-template](https://www.npmjs.com/package/@dingos/pwa-kit-template)
