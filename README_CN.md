# 基于 AI 的 Git 提交消息生成器

[English](./README.md)

[![PyPI version](https://badge.fury.io/py/aimsg.svg)](https://badge.fury.io/py/aimsg)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.7+](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/)

一个基于 AI 模型，根据 Git 仓库变更自动生成提交信息的命令行工具。

## 特性

- 🤖 广泛的模型支持：
  - OpenAI
  - Anthropic
  - Google
  - DeepSeek
  - Aliyun
  - iFlytek
  - Zhipu
  - Baidu
  - Moonshot
  - Tencent
  - ByteDance
  - Replicate
  - Together AI
- 🔧 支持自定义 API base
- 🔧 支持自定义模型集成
- 📝 符合 Conventional Commits 规范
- 🎯 可自定义提示词模板
- 🔑 安全的配置管理

## 安装

### 使用 pipx（推荐）

```bash
# 如果还没安装pipx，先安装它
brew install pipx
pipx ensurepath

# 安装 aimsg
pipx install aimsg

# 升级 aimsg 到最新版
pipx upgrade aimsg
```

### 使用 pip

```bash
pip install aimsg
```

## 快速开始

1. 使用您偏好的模型和 API 密钥初始化：

```bash
aimsg init
```

2. 暂存更改并生成提交信息：

```bash
git add .
aimsg commit
```

3. 获取帮助或版本信息：

```bash
# 显示版本
aimsg --version

# 显示所有可用命令
aimsg --help

# 显示特定命令的帮助信息
aimsg model --help
aimsg commit --help

# 显示当前配置
aimsg current
```

## 配置

`aimsg` 的配置按以下优先级顺序生效：

1. 项目级 `.env` 文件（最高优先级）

```bash
AIMSG_API_KEY=your_api_key
AIMSG_API_BASE=your_api_base
AIMSG_MODEL=your_model
AIMSG_PROMPT=your_prompt
```

2. 环境变量（次优先级）

```bash
export AIMSG_API_KEY=your_api_key
export AIMSG_API_BASE=your_api_base
export AIMSG_MODEL=your_model
export AIMSG_PROMPT=your_prompt
```

3. 通过 `aimsg init` 的全局配置（最低优先级，默认）

```bash
aimsg init

# 在 ~/.config/aimsg/config.json 创建默认设置：
# - model: 你的模型
# - api_base: 你的 API base
# - api_key: 你的 API 密钥
# - prompt: 默认提示词模板
# - custom_models: 自定义模型列表
```

## 模型管理

```bash
# 列出可用模型
aimsg model list

# 添加自定义模型
aimsg model add my-model https://api.example.com/v1

# 移除自定义模型
aimsg model remove my-model
```

## 提示词管理

```bash
# 自定义提交信息提示词模板
aimsg prompt

# 重置为默认提示词模板
aimsg reset-prompt

```
默认提示词模版：
```
Based on the following git diff, generate a concise and descriptive commit message that follows conventional commits format.
Focus on the "what" and "why" of the changes.
Start with a type (feat, fix, docs, style, refactor, perf, test, build, ci, chore).
Do not include scope.
Limit the first line to 72 characters.
Add a blank line followed by a more detailed description if necessary.
```

默认提示词模板指导 AI：

- 遵循 conventional commits 格式
- 关注变更的"是什么"和"为什么"
- 保持首行在 72 个字符以内
- 必要时添加详细描述

## 默认 API 提供商

- OpenAI: `https://api.openai.com/v1`
- Anthropic: `https://api.anthropic.com/v1`
- Google: `https://generativelanguage.googleapis.com/v1`
- DeepSeek: `https://api.deepseek.com/v1`
- 阿里云: `https://dashscope.aliyuncs.com/api/v1`
- 讯飞: `https://spark-api.xf-yun.com/v3.1`
- 智谱: `https://open.bigmodel.cn/api/v1`
- 百度: `https://aip.baidubce.com/rpc/2.0/ai_custom/v1/wenxinworkshop`
- Moonshot: `https://api.moonshot.cn/v1`
- 腾讯: `https://hunyuan.cloud.tencent.com/hyllm/v1`
- 字节跳动: `https://api.doubao.com/v1`
- Replicate: `https://api.replicate.com/v1`
- Together AI: `https://api.together.xyz/v1`

## 许可证

MIT
