# Git 提交规范

## 目录

- [Git 提交规范](#git-提交规范)
  - [目录](#目录)
  - [简介](#简介)
  - [提交消息的格式](#提交消息的格式)
    - [默认格式](#默认格式)
    - [合并分支提交格式](#合并分支提交格式)
    - [撤销提交格式](#撤销提交格式)
    - [初始提交](#初始提交)
  - [详细说明](#详细说明)
    - [类型](#类型)
      - [功能相关](#功能相关)
      - [代码质量改进](#代码质量改进)
      - [开发过程相关](#开发过程相关)
      - [项目构建和运维](#项目构建和运维)
    - [范围](#范围)
    - [重大变更提示符](#重大变更提示符)
    - [简要描述](#简要描述)
    - [正文](#正文)
    - [尾注](#尾注)
  - [提交示例](#提交示例)
    - [基础示例](#基础示例)
    - [带正文的示例](#带正文的示例)
    - [性能和重构示例](#性能和重构示例)
    - [提交信息生成工具](#提交信息生成工具)
    - [VS Code 扩展](#vs-code-扩展)
    - [配置示例](#配置示例)
  - [参考资料](#参考资料)

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

#### 功能相关

- `feat`：添加新的功能。
- `fix`：修复一个 Bug。

#### 代码质量改进

- `refactor`：重写或重构代码，但是并没有改变任何 API 的行为。
- `perf`：一种特殊的重构，提高了性能，但是没有改变任何 API 的行为。

#### 开发过程相关

- `style`：不改变代码或文档的含义（例如处理空格、格式、缺少分号等）。
- `test`：添加缺少的测试或纠正现有的测试。
- `docs`：只改变文档或代码中的注释。

#### 项目构建和运维

- `build`：改变构建组件，例如构建工具、CI pipeline、依赖、项目版本等。
- `ops`：改变运营组件，例如基础设施、部署、备份、恢复等。
- `chore`：杂项提交，即对整个项目意义不大的提交，例如修改 `.gitignore`。

### 范围

`[范围]` 字段能够提供额外的上下文信息，用于说明此次提交影响的具体模块或组件，但该字段不强制要求填写。

常见的范围示例：

- **前端项目**：`auth`、`dashboard`、`api`、`ui`、`router` 等
- **后端项目**：`user`、`order`、`payment`、`database` 等
- **文档项目**：`readme`、`tutorial`、`api-docs` 等
- **工具项目**：`cli`、`config`、`build` 等

> [!important]
>
> 范围应该是项目中有意义的模块或组件名称。如果项目文档中没有明确定义范围规范，建议与团队协商确定一套统一的范围命名约定。

> [!warning]
>
> 不要使用 Issue 标识符作为范围。

### 重大变更提示符

重大变更应在首行的 `:` 前用 `!` 表示，但这是可选的。

> [!important]
>
> `!` 应使用英文半角符号。

### 简要描述

简要描述此次更改的内容，该字段有以下注意事项：

- **强制要求填写**。
- **长度限制**：建议不超过 50 个字符，最长不超过 72 个字符。
- **语言风格**：使用命令式的语气和现在时，例如：
  - ✅ 正确：`add user authentication`
  - ❌ 错误：`added user authentication`（过去时）
  - ❌ 错误：`adds user authentication`（第三人称单数）
- **首字母**：使用小写字母开头。
- **标点符号**：不要在句尾使用句号 `。` 或点号 `.`。
- **内容要求**：应该能够回答"如果应用这个提交，它将..."这个问题。

### 正文

正文部分应包括做出改变的动机并将其与之前的行为进行对比，为读者提供更多的上下文信息。

- **可选部分**。
- **语言风格**：使用命令式的语气和现在时。
- **内容建议**：
  - 解释为什么需要这个改动
  - 描述改动的影响范围
  - 说明与之前行为的区别
- **Issue 关联**：可以在这里使用 Issue 标识符并说明改变与 Issue 的关系。

### 尾注

尾注部分应包含有关重大变更的任何信息，以及此提交所涉及的 Issue 标识符。

- **可选部分**。
- **Issue 引用**：通过 Issue 的 ID 引用相关 Issue，格式如：
  - `Closes #123`（关闭 Issue）
  - `Fixes #123`（修复 Issue）
  - `Refs #123`（引用 Issue）
- **重大变更**：与重大变更有关的信息应以 `BREAKING CHANGE:` 开头。

> [!note]
>
> 与重大变更有关的信息应在 `BREAKING CHANGE:` 后以一个空格或两行空行开始。

## 提交示例

### 基础示例

- ```shell
  feat: add email notifications on new direct messages
  ```

- ```shell
  feat(shopping cart): add the amazing button
  ```

- ```shell
  fix(shopping-cart): prevent order an empty shopping cart
  ```

- ```shell
  fix(api): fix wrong calculation of request body checksum
  ```

### 带正文的示例

- ```shell
  feat!: remove ticket list endpoint
  
  refers to JIRA-1337
  
  BREAKING CHANGES: ticket endpoints no longer supports list all entities.
  ```

- ```shell
  fix: add missing parameter to service call
  
  The error occurred because of <reasons>.
  ```

### 性能和重构示例

- ```shell
  perf: decrease memory footprint for determine unique visitors by using HyperLogLog
  ```

- ```shell
  build: update dependencies
  ```

- ```shell
  build(release): bump version to 1.0.0
  ```

- ```shell
  refactor: implement fibonacci number calculation as recursion
  ```

- ```shell
  style: remove empty line
  ```

## 工作流建议

### 提交频率

- **小步快走**：频繁进行小的、有逻辑的提交，而不是一次性提交大量改动。
- **功能完整性**：每个提交应该包含一个完整的、可测试的改动。
- **避免混合**：不要在一个提交中混合不同类型的改动（如功能开发和代码格式化）。

### 提交前检查清单

- [ ] 代码已经过本地测试
- [ ] 提交信息遵循规范格式
- [ ] 只包含相关的文件改动
- [ ] 敏感信息已被移除
- [ ] 代码符合项目的编码标准

### 团队协作建议

- **统一标准**：团队内部应统一提交规范，可以使用工具（如 commitlint）进行自动检查。
- **代码审查**：在合并前进行代码审查，确保提交质量。
- **分支策略**：配合适当的分支策略（如 Git Flow）使用规范的提交信息。

### 常见错误和最佳实践

#### 常见错误

- ❌ **类型选择错误**：`fix: add new feature` 应该使用 `feat` 类型
- ❌ **描述不清晰**：`fix: bug` 应该具体说明修复了什么问题
- ❌ **时态错误**：`added new feature` 应该使用 `add new feature`
- ❌ **混合改动**：一个提交既有功能开发又有代码格式化
- ❌ **提交过大**：包含多个不相关的改动

#### 最佳实践

- ✅ **原子性提交**：每个提交只做一件事情
- ✅ **描述具体**：说明做了什么，而不是为什么做
- ✅ **测试完整**：提交前确保改动通过测试
- ✅ **保持一致**：团队内统一使用相同的规范

## 特殊情况说明

### 文档为中心的项目

在实际工作和学习过程中，并非每个项目都是软件开发，比如有些项目以文档为中心。对于此类项目，作出以下特别声明：

- `feat` 只能用于与代码有关的功能提交。
- `refactor` 可扩展为对文档的重写或重构，但是并没有改变文档的核心内容和信息，比如目录重组、章节重排、优化表述方式等。
- 所有内容的实质性变更（即表达的意思发生了改变，比如新增、删除等）全部使用 `docs`。
- 对于文档内容中错误的修改，统一使用 `docs`。
- 其余类型含义保持不变。

### 配置文件和环境设置

对于主要涉及配置文件、环境设置或项目结构调整的提交：

- **配置文件修改**：
  - 新增配置项：`feat(config): add new database connection settings`
  - 修改现有配置：`fix(config): correct redis timeout value`
  - 配置文件重构：`refactor(config): reorganize environment variables`

- **环境和部署相关**：
  - Docker 配置：`build(docker): update base image to node:18`
  - CI/CD 管道：`build(ci): add automated testing pipeline`
  - 部署脚本：`ops(deploy): add health check endpoint`

### 依赖管理

对于包管理和依赖相关的变更：

- **添加依赖**：`build(deps): add lodash for utility functions`
- **更新依赖**：`build(deps): update react to v18.2.0`
- **移除依赖**：`build(deps): remove unused axios dependency`
- **安全更新**：`fix(deps): update vulnerable packages`

### 多语言项目

对于包含多种编程语言或技术栈的项目：

- 使用范围来区分不同的技术栈：
  - `feat(frontend): add user dashboard`
  - `fix(backend): resolve database connection issue`
  - `docs(api): update REST API documentation`

### 学习和实验项目

对于个人学习、实验或概念验证项目：

- **学习笔记**：`docs(learning): add notes on React hooks`
- **实验代码**：`feat(experiment): try new authentication approach`
- **练习项目**：`feat(practice): implement basic calculator`
- **代码示例**：`docs(example): add usage examples for API`

### 版本发布和里程碑

对于版本发布相关的提交：

- **版本发布**：`build(release): bump version to v1.2.0`
- **更新日志**：`docs(changelog): add v1.2.0 release notes`
- **版本标签**：通常由自动化工具处理，但如果手动操作：`chore(release): prepare for v1.2.0 release`

### 紧急修复

对于生产环境的紧急修复：

- **热修复**：`fix(hotfix): prevent null pointer exception in login`
- **安全补丁**：`fix(security): patch XSS vulnerability in user input`
- **回滚操作**：`fix(rollback): revert problematic feature deployment`

> [!tip]
>
> 对于紧急修复，建议在提交信息中包含更多上下文信息，便于后续追踪和审计。

## 工具推荐

### 提交信息规范检查

- **commitlint**：自动检查提交信息是否符合规范

  ```shell
  npm install --save-dev @commitlint/cli @commitlint/config-conventional
  ```

- **husky**：Git hooks 管理工具，可以在提交前自动运行 commitlint

  ```shell
  npm install --save-dev husky
  ```

### 提交信息生成工具

- **commitizen**：交互式提交信息生成工具

  ```shell
  npm install -g commitizen cz-conventional-changelog
  ```

- **gitmoji-cli**：使用 emoji 的提交信息工具（可选）

  ```shell
  npm install -g gitmoji-cli
  ```

### VS Code 扩展

- **Conventional Commits**：VS Code 扩展，提供提交信息模板
- **Git Graph**：可视化 Git 历史，更好地查看提交规范的效果
- **GitLens**：增强 Git 功能，包括提交信息预览

### 配置示例

`.commitlintrc.js` 配置文件示例：

```javascript
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'type-enum': [2, 'always', [
      'feat', 'fix', 'docs', 'style', 'refactor',
      'perf', 'test', 'build', 'ops', 'chore'
    ]],
    'subject-max-length': [2, 'always', 72],
    'subject-case': [2, 'always', 'lower-case']
  }
};
```

## 参考资料

- [Conventional Commits Cheatsheet](https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13)
- [Conventional Commits 官方规范](https://www.conventionalcommits.org/)
- [Angular 提交规范](https://github.com/angular/angular/blob/main/CONTRIBUTING.md#-commit-message-format)
- [语义化版本控制](https://semver.org/lang/zh-CN/)
