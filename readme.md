# sapegin/mrm [![explain]][source] [![translate-svg]][translate-list]

<!-- [![size-img]][size] -->

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/Source-Explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list
[size-img]: https://packagephobia.now.sh/badge?p=Name
[size]: https://packagephobia.now.sh/result?p=Name

「 命令行工具，以帮助您保持配置（`package.json`，`.gitignore`，`.eslintrc`等等）。让您的开源项目同步。 」

[中文](./readme.md) | [english](https://github.com/sapegin/mrm)

---

## 校对 ✅

<!-- doc-templite START generated -->
<!-- repo = 'sapegin/mrm' -->
<!-- commit = 'f4892d3eee6bc52b3805181f2b813e8ea9eaba7f' -->
<!-- time = '2018-10-09' -->
翻译的原文 | 与日期 | 最新更新 | 更多
---|---|---|---
[commit] | ⏰ 2018-10-09 | ![last] | [中文翻译][translate-list]

[last]: https://img.shields.io/github/last-commit/sapegin/mrm.svg
[commit]: https://github.com/sapegin/mrm/tree/f4892d3eee6bc52b3805181f2b813e8ea9eaba7f

<!-- doc-templite END generated -->

### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[If help, **buy** me coffee —— 营养跟不上了，给我来瓶营养快线吧! 💰](https://github.com/chinanf-boy/live-need-money)

---

# Mrm

[![Build Status](https://travis-ci.org/sapegin/mrm.svg)](https://travis-ci.org/sapegin/mrm)
[![npm](https://img.shields.io/npm/v/mrm.svg)](https://www.npmjs.com/package/mrm)

命令行工具，以帮助您的开源项目保持配置（`package.json`，`.gitignore`，`.eslintrc`等等)同步。

## 特征

- 如果您不想要它，不会覆盖您的数据
- 最小的更改：将保留原始文件格式或从 EditorConfig 中读取样式
- 最小配置：将尝试从项目本身或从环境推断配置
- 包含一堆[可定制 任务](#%E4%BB%BB%E5%8A%A1)
- 使用 JSON，YAML，INI，Markdown 和隔行格式文件的工具
- 容易编写[属于你的 任务](#%E7%BC%96%E5%86%99%E8%87%AA%E5%B7%B1%E7%9A%84%E4%BB%BB%E5%8A%A1)
- 通过 npm 分享 任务，并将它们分组到[预设](#%E8%87%AA%E5%AE%9A%E4%B9%89%E9%A2%84%E8%AE%BE)

![](https://d3vv6lp55qjaqc.cloudfront.net/items/1g0e2M3m2Y3j0m3B3n1t/Image%202017-06-20%20at%209.00.39%20PM.png)

## 目录

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [动机](#%E5%8A%A8%E6%9C%BA)
- [安装](#%E5%AE%89%E8%A3%85)
- [用法](#%E7%94%A8%E6%B3%95)
- [通过 npx 使用](#%E9%80%9A%E8%BF%87-npx-%E4%BD%BF%E7%94%A8)
- [配置](#%E9%85%8D%E7%BD%AE)
- [任务](#%E4%BB%BB%E5%8A%A1)
- [编写自己的任务](#%E7%BC%96%E5%86%99%E8%87%AA%E5%B7%B1%E7%9A%84%E4%BB%BB%E5%8A%A1)
- [通过 npm 分享任务](#%E9%80%9A%E8%BF%87-npm-%E5%88%86%E4%BA%AB%E4%BB%BB%E5%8A%A1)
- [自定义预设](#%E8%87%AA%E5%AE%9A%E4%B9%89%E9%A2%84%E8%AE%BE)
- [配置解析规则](#%E9%85%8D%E7%BD%AE%E8%A7%A3%E6%9E%90%E8%A7%84%E5%88%99)
- [任务解析规则](#%E4%BB%BB%E5%8A%A1%E8%A7%A3%E6%9E%90%E8%A7%84%E5%88%99)
- [常问问题](#%E5%B8%B8%E9%97%AE%E9%97%AE%E9%A2%98)
- [更改日志](#%E6%9B%B4%E6%94%B9%E6%97%A5%E5%BF%97)
- [贡献](#%E8%B4%A1%E7%8C%AE)
- [作者和许可证](#%E4%BD%9C%E8%80%85%E5%92%8C%E8%AE%B8%E5%8F%AF%E8%AF%81)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 动机

大多数可用工具都是基于模板的。模板方法适用于新项目生成，但不适用于更新。Mrm 的方法更接近于[codemods](https://github.com/facebook/codemod)，而不是模版。

在我的文章中阅读更多内容[用 Mrm 自动化 开源项目配置](http://blog.sapegin.me/all/mrm)，或看[Mrm 介绍](https://www.youtube.com/watch?v=5tHfAf4bRcM)。

## 安装

```
npm install -g mrm
```

## 用法

打印可用任务列表：

```shell
mrm
```

运行任务或别名

```shell
mrm gitignore
mrm license
```

运行多个任务：

```shell
mrm gitignore license
```

覆盖配置选项（或在没有配置文件的情况下运行）：

```shell
mrm license --config:name "Gandalf the Grey" --config:email "gandalf@middleearth.com" --config:url "http://middleearth.com"
```

自定义配置和任务文件夹：

```shell
mrm license --dir ~/unicorn
```

从预设中运行任务（全局安装`mrm-preset-unicorn`的 npm 包，阅读更多[关于 预设](#%E8%87%AA%E5%AE%9A%E4%B9%89%E9%A2%84%E8%AE%BE)的信息）：

```shell
mrm license --preset unicorn
```

## 通过 npx 使用

如果你有 npm 5.3 或更新版本，你可以在没有安装的情况下使用 mrm：

```shell
npx mrm
npx mrm gitignore
npx mrm license --config:name "Gandalf the Grey" --config:email "gandalf@middleearth.com" --config:url "http://middleearth.com"
```

## 配置

创建`~/.mrm/config.json`或`~/dotfiles/mrm/config.json`：

```json5
{
  indent: 'tab', // “tab”或空格数
  readmeFile: 'Readme.md', // 自述文件的名称
  licenseFile: 'License.md', // 许可证文件名
  aliases: {
    // 同时运行多个任务的别名
    node: ['license', 'readme', 'editorconfig', 'gitignore']
  }
}
```

看到[任务 文档](https://github.com/sapegin/mrm-tasks)中可用的配置选项。

_不需要配置文件，也可以通过命令行传递配置选项。默认任务将尝试从你的 npm 和 Git 配置中[读取 数据](https://github.com/sapegin/user-meta)。_

## 任务

默认情况下,包含这些任务：

<!-- textlint-disable terminology -->

- [codecov](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-codecov)
- [contributing](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-contributing)
- [editorconfig](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-editorconfig)
- [eslint](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-eslint)
- [gitignore](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-gitignore)
- [jest](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-jest)
- [license](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-license)
- [lint-staged](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-lint-staged)
- [package](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-package)
- [prettier](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-prettier)
- [readme](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-readme)
- [semantic-release](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-semantic-release)
- [styleguidist](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-styleguidist)
- [stylelint](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-stylelint)
- [travis](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-travis)
- [typescript](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-task-typescript)

<!-- textlint-enable -->

## 编写自己的任务

创建任一个`~/.mrm/<TASK>/index.js`或`~/dotfiles/mrm/<TASK>/index.js`。其中的`<TASK>`是您的任务，将覆盖默认的相同任务。

最简单的任务，可能如下所示：

```js
// 使用新行分隔文本文件的MRM模块
const {lines} = require('mrm-core');

function task() {
  // 如果它存在，则读取.gitignore
  lines('.gitignore')
    // 添加文件中不存在的行，
    // 但保留所有现有行
    .add(['node_modules/', '.DS_Store'])
    // 更新或创建文件
    .save();
}

task.description = 'Adds .gitignore';
module.exports = task;
```

通过添加`async`关键字或返回`Promise`，任务也可以是异步的。

```js
async function task() {}

// 或
function task() {
  return new Promise(() => {});
}
```

如果您的任务具有依赖项（例如`mrm-core`)，你应该初始化`mrm`文件夹，作为 npm 模块并列出您的依赖项：

```bash
cd ~/.mrm # or cd ~/dotfiles/mrm
npm init -y
npm install --save mrm-core
```

[mrm-core](https://github.com/sapegin/mrm-core)是一个为编写 Mrm 任务而创建的实用程序库，它具有使用常见配置文件（JSON，YAML，INI，Markdown），npm 依赖项等的功能。

我们来看一个更复杂的任务：

```js
const {
  // JSON文件
  json,
  // 包装袋
  packageJson,
  // 新行分隔文本文件
  lines,
  // 安装NPM包
  install
} = require('mrm-core');

function task(config) {
  // 任务选项
  // mrm eslint--config:name 比萨
  const {name, eslintPreset} = config
    .defaults({
      // 默认值
      eslintPreset: 'eslint:recommended'
    })
    // 需要选项
    .require('name')
    .values();

  // 使用来自NPM的自定义预设包
  const packages = ['eslint'];
  if (eslintPreset !== 'eslint:recommended') {
    packages.push(`eslint-config-${eslintPreset}`);
  }

  // 创建或更新 .eslintignore
  lines('.eslintignore')
    .add(['node_modules/'])
    .save();

  // 阅读 project 的 package.json
  const pkg = packageJson();

  pkg
    // 添加 lint 脚本
    .setScript('lint', 'eslint . --cache --fix')
    // 添加预测试脚本
    .prependScript('pretest', 'npm run lint')
    .save();

  // read.eslintrc 如果存在
  const eslintrc = json('.eslintrc');

  // 如果项目依赖于 babel，则使用 babel解析器
  if (pkg.get('devDependencies.babel-core')) {
    const parser = 'babel-eslint';
    packages.push(parser);
    eslintrc.merge({parser});
  }

  // 设置预置
  eslintrc.set('extends', eslintPreset).save();

  // 安装NPM依赖项
  install(packages);
}

task.description = 'Adds ESLint';
module.exports = task;
```

`mrm-core`还有更多的方法- 查看[文档](https://github.com/sapegin/mrm-core#api)和[默认任务](https://github.com/sapegin/mrm-tasks)。

## 通过 npm 分享任务

共享任务的基本文件结构如下所示：

```
.
├── index.js
├── package.json
```

`index.js`与描述的相同[上一小节](#%E7%BC%96%E5%86%99%E8%87%AA%E5%B7%B1%E7%9A%84%E4%BB%BB%E5%8A%A1)。而且`package.json`看起来像这样：

```json
{
  "name": "mrm-task-unicorn",
  "version": "0.1.0",
  "description": "Unicorn task for Mrm",
  "author": {
    "name": "Artem Sapegin",
    "url": "http://sapegin.me"
  },
  "homepage": "https://github.com/sapegin/mrm-tasks/packages/mrm-task-unicorn",
  "repository": "sapegin/mrm-tasks",
  "license": "MIT",
  "engines": {
    "node": ">=4"
  },
  "main": "index.js",
  "files": ["index.js"],
  "keywords": ["mrm", "mrm-task", "unicorn"],
  "dependencies": {
    "mrm-core": "^2.1.3"
  }
}
```

包名应该遵循以下模式：`mrm-task-<TASK>`，否则您必须在运行任务时键入完整的包名称：

```
mrm unicorn # mrm-task-unicorn
mrm @mycompany/unicorn-task # @mycompany/unicorn-task
```

## 自定义预设

Preset(预设) 是一个包含配置和任务的 npm 包（或目录）。

文件结构如下所示：

```
.
├── task1
│   └── index.js
├── task2
│   └── index.js
├── config.json
├── package.json
```

而，`package.json`看起来像这样：

```json
{
  "name": "mrm-preset-default",
  "version": "0.1.0",
  "description": "Common tasks for Mrm",
  "author": {
    "name": "Artem Sapegin",
    "url": "http://sapegin.me"
  },
  "homepage": "https://github.com/sapegin/mrm-tasks/packages/mrm-preset-default",
  "repository": "sapegin/mrm-tasks",
  "license": "MIT",
  "engines": {
    "node": ">=4"
  },
  "main": "config.json",
  "files": ["config.json", "*/index.js"],
  "keywords": ["mrm", "mrm-task", "mrm-preset"],
  "dependencies": {
    "mrm-core": "^2.1.3",
    "mrm-task-gitignore": "^0.1.0"
  }
}
```

见上面的[编写自己的任务](#%E7%BC%96%E5%86%99%E8%87%AA%E5%B7%B1%E7%9A%84%E4%BB%BB%E5%8A%A1)部分，去学习如何编写 Mrm 任务。要将任务添加到预设，请将其添加到在预设文件夹中的`<TASK>/index.js`文件。

如果要使用 npm（或任何默认任务）中的任务，则应将其作为依赖项包含在内。这样您就可以确保，始终拥有适用项目的任务版本。

例如，如果要使用`mrm-task-gitignore`任务，你需要创建一个预设包文件夹中的`gitignore/index.js`文件：

```js
module.exports = require('mrm-task-gitignore');
```

包名应该遵循以下模式：`mrm-preset-<TASK>`，否则您必须在运行任务时键入完整的包名称：

```
mrm license --preset unicorn # mrm-preset-unicorn
mrm license --preset @mycompany/unicorn-preset # @mycompany/unicorn-preset
```

## 配置解析规则

- `<DIR>/config.json`，如果已传递`--dir <DIR>`命令行选项
- `$HOME/dotfiles/mrm/config.json`
- `$HOME/.mrm/config.json`

如果你传递了`--preset <PRESET>`命令行选项，那么唯一的任务目录将是：

- `mrm-preset-<PRESET>/config.json`

## 任务解析规则

- `<DIR>/<TASK>/index.js`，如果已传递`--dir <DIR>`命令行选项
- `$HOME/dotfiles/mrm/<TASK>/index.js`
- `$HOME/.mrm/<TASK>/index.js`
- `mrm-task-<TASK>/index.js`，这里的`mrm-task-<TASK>`是一个 npm 包名称
- `<TASK>`在[mrm-preset-default](https://github.com/sapegin/mrm-tasks/tree/master/packages/mrm-preset-default)

如果你传递了`--preset <PRESET>`命令行选项，那么唯一的任务目录将是：

- `mrm-preset-<PRESET>/<TASK>/index.js`

## 常问问题

### 如何使用 Mrm 与 Lerna？

为[Lerna](https://github.com/lerna/lerna)库中的每个包运行任务：

```bash
./node_modules/.bin/lerna exec -- mrm <TASK>
```

### 如何推断用户元数据，如用户名或电子邮件？

使用[user-meta](https://github.com/sapegin/user-meta)包，从`.npmrc`或`.gitconfig`中读取用户名，电子邮件和 URL：

```js
const meta = require('user-meta');
module.exports = function task(config) {
  const {name, email, url} = config
    .defaults(meta)
    .require('name', 'email', 'url')
    .values();
  /* ... */
};
```

### 如何推断 GitHub 用户名？

使用[git-username](https://github.com/jonschlinkert/git-username)包：

```js
const gitUsername = require('git-username');
module.exports = function task(config) {
  const {github} = config
    .defaults({
      github: gitUsername()
    })
    .require('github')
    .values();
  /* ... */
};
```

## 更改日志

更改日志可以在上找到[Releases 页面](https://github.com/sapegin/mrm/releases)。

## 贡献

欢迎每个人做出贡献。请花一点时间来回顾一下[contributing 指南](Contributing.md)。

## 作者和许可证

[Artem Sapegin](http://sapegin.me)和[帮助者](https://github.com/sapegin/mrm/graphs/contributors)。

MIT 许可证，请参阅随附的[License.md](License.md)文件。
