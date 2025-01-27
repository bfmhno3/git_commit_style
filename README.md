# Git 提交规范

## 简介

本仓库是用于我（bfmhno3）个人项目的 Git 提交规范指南，旨在提高提交信息的一致性和项目历史的可读性与可追溯性。

## 提交消息的格式

### 默认格式

```shell
<类型>([范围])[!]: <简要描述>
# 空行
[正文]
# 空行
[尾注]
```

> [!note]
>
> `<>` 代表**必要信息**，每次提交中都应当编写这部分信息。
>
> `[]` 代表**可选信息**，不强制要求编写，但提交者编写这部分信息更好。
>
> `#` 表示注释，此处只用作说明，在实际提交时不必添加。

> [!important]
>
> `()`、`:` 以及 `!` 均应使用英文**半角**符号。

### 合并分支提交格式

```shell
Merge branch '<branch_name>'
```

与 Git 默认的合并消息格式保持一致。

### 撤销提交格式

```shell
Revert "<reverted commit subject line>"
```

与 Git 默认的撤销消息格式保持一致。

### 初始提交

```shell
chore: init
```

## 详细说明

### 类型

+ 与 API 有关的更改：
  + `feat`：添加新的功能或移除旧的功能。
  + `fix`：修复一个 Bug。
+ `refactor`：重写或重构代码，但是并没有改变任何 API 的行
  + `perf`：一种特殊的重构 `refactor`，提高了性能，但是没有改变任何 API 的行为。
+ `style`：不改变代码或文档的含义（例如处理空格、格式、缺少分号等）。
+ `test`：添加缺少的测试或纠正现有的测试。
+ `docs`：只改变文档或代码中的注释。
+ `build`：改变构建组件，例如构建工具、CI pipeline、依赖、项目版本等。
+ `ops`：改变运营组件，例如基础设施、部署、备份、恢复等。
+ `chore`：杂项提交，即对整个项目意义不大的提交，例如修改 `.gitignore`。

### 范围

`[范围]` 字段能够提供额外的上下文信息，但该字段不强制要求填写。

> [!important]
>
> 这个字段的内容应该由某个具体的项目提供，如果项目文档中没有具体说明这个字段应该填写的内容，则不应该填写该字段。
>
> 如果提供了，则推荐填写。

> [!warning]
>
> 不要使用 Issue 标识符。

### 重大变更提示符

重大变更应在首行的 `:` 前用 `!` 表示，但这是可选的。

> [!important]
>
> `!` 应使用英文半角符号。

### 简要描述

简要描述此次更改的内容，该字段有以下注意事项：

+ 强制要求填写。
+ 使用命令式的语气和现在时，例如不要使用 `刚在修改了...` 而是使用 `修改了...`，不要使用 `这项更改将会...` 而是 `这项更改会...`。
+ 不要在句尾使用句号 `。` 或点号 `.`。

### 正文

正文部分应包括做出改变的动机并将其与之前的行为进行对比。

+ 可选部分。
+ 使用命令式的语气和现在时。
+ 在这里可以使用 Issue 标识符并说明改变与 Issue 的关系（即是否修复该 Issue等）。

### 尾注

页脚部分应包含有关重大变更的任何信息，以及此提交所涉及的 Issue 标识符。

+ 可选部分。
+ 通过 Issue 的 ID 引用 Issue。
+ 与重大变更有关的信息应以 `BREAKING CHANGES:` 开头。

> [!note]
>
> 与重大变更有关的信息应在 `BREAKING CHANGES:` 后以一个空格 ` ` 或两行空行开始。

## 例子

+ ```shell
  feat: add email notifications on new direct messages
  ```

+ ```shell
  feat(shopping cart): add the amazing button
  ```

+ ```shell
  feat!: remove ticket list endpoint
  
  refers to JIRA-1337
  
  BREAKING CHANGES: ticket endpoints on longer supports list all entities.
  ```

+ ```shell
  fix(shopping-cart): prevent order an empty shopping cart
  ```

+ ```shell
  fix(api): fix wrong calculation of request body checksum
  ```

+ ```shell
  fix: add missing parameter to service call
  
  The error occurred because of <reasons>.
  ```

+ ```shell
  perf: decrease memory footprint for determine unique visitors by using HyperLogLog
  ```

+ ```shell
  build: update dependencies
  ```

+ ```
  build(release): bump version to 1.0.0
  ```

+ ```
  refactor: implement fibonacci number calculationn as recursion
  ```

+ ```
  style: remove empty line
  ```

## 参考资料

+ [conventional-commits-cheatsheet.md](https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13)
+ https://www.conventionalcommits.org/
