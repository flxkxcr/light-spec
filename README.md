# 轻量规范驱动开发 (LSDD, Lightweight Spec-Driven Development)

## 背景与痛点

- 现有主流的 spec 驱动开发框架，在开发者已有清晰思路时显得繁琐。
- 希望建立一种**灵活、可追溯、低 token 消耗**的开发模式，以**每个feature一份，且人类可以随时介入**的自生长的 Markdown 文档为核心，支持 AI 按需读取和更新，实现轻量级的规范驱动开发方案。

## 核心spec文档结构

**每个需求**对应一份独立的 `.md` 文档，包含 **5 个固定一级标题**：

1. 需求分析
2. 架构设计
3. 测试标准
4. 任务清单
5. 日志

> 用户可手工编写部分内容，也可让 AI 按需补充。


## 可追溯与冲突检测机制

使用 YAML Frontmatter 记录元信息
在每个 `.md` 文档开头增加 YAML 头，字段示例：

```markdown
---
id: feature-图片转码-png_to_jpg      # 唯一ID，与文件名一致
title: 图片转码功能(png -> jpg)
keywords: [图片, 转码, png, jpg]
summary: 实现png图片转码为jpg的功能
status: in_progress                 # in_progress | done
git_commit: a1b2c3d                 # git commit 之后，由用户手动填写，或者让AI自己commit自己填写
dependencies: [feature-database]    # 该功能是基于feature-database功能实现的，智能体需要阅读feature-database.md文件，理解实现思路
---
```

## 使用方法 (OpenCode)
1. 将 `.opencode` 目录中的内容，全部复制进你项目的 `.opencode` 目录中
2. 将整个 `.light-spec-rules` 目录复制到你的项目的根目录中
3. 新建 `.light-spec` 目录
4. 新建 `feature1.md` 文件，按照 `.light-spec-rules/spec-template.md` 的结构编写
5. 打开 opencode，按照步骤，依次执行 `/lsdd-requirement`, `/lsdd-design`, `/lsdd-testing-standards`, `/lsdd-tasks`, `/lsdd-execute`。来完成一个feature的编写。
6. 确认功能正确，并且git commit后，在 `feature1.md` 文件的 YAML frontmatter 部分，补充 git_commit 字段和 status 字段。至此，feature1正式开发完成。
7. 开发下一个功能 feature2

## 重点
- 每个命令，都可以由人工代替编写spec文档，无需每一步都走AI流程
- 每个feature，只有一份spec文档，轻量级。
- 每个spec文档，都有 dependencies 字段，用于人工标记feature之间的依赖关系，智能体在读spec文件时，会递归向上溯源整个依赖链。
  - 开发者可以选择不标记依赖链，降低读取文件的token消耗



## 命令大全

### 制定项目规范
`/lsdd-constitution <用户意图>` : 智能体会根据你的意图，与你讨论各种开发规范和细节，最终制定一份 `.light-spec-rules/constitution.md` 文件，之后的每个命令，都会先阅读这份文件，再执行。

### 初始化项目 (TODO)
`lsdd-init <用户意图>`

### 需求分析
`/lsdd-requirement <spec-file>.md <用户意图，例如：开发一个图片转码功能，支持从PNG转到JPG>` : 智能体会与你讨论，精确分析需求，并修改文档的 `需求分析` 部分。提示词部分不可为空。

### 架构设计
`/lsdd-design <spec-file>.md <用户意图，例如：开发一个图片转码功能，支持从PNG转到JPG>` : 智能体会与你讨论出最优的架构设计方案，然后修改文档的 `架构设计` 部分。提示词可为空。

### 制定测试标准
`/lsdd-testing-standards <spec-file>.md <用户意图>`: 智能体会与你讨论出具体需要编写哪些测试用例，每个测试用例的作用，然后修改文档的 `测试标准` 部分。提示词可为空。

### 制定任务列表
`lsdd-tasks <spec-file>.md <用户意图>`: 智能体会拆分实现方案，拆分成列表的每一项，并且使用复选框的方式表示，然后写入到文档的 `任务清单` 部分。

### 按照任务列表执行，然后记录日志
`lsdd-execute <spec-file>.md <用户意图>`: 智能体根据任务清单，立即执行所有任务，并进行测试。若测试成功，则勾选复选框，并记录测试结果以及智能体日志。

### Git Commit (TODO)
`lsdd-git-commit <spec-file>.md <用户意图>`: 提交git commit，智能体根据spec-file，总结出commit message，然后提交。接着修改spec-file的YAML的status字段，修改为 `done`，并记录此次提交的 git commit hash到 `git_commit` 字段

