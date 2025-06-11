# Claude Code 完整使用指南

Claude Code是Anthropic开发的智能编程助手工具，它直接在终端中运行，能够理解代码库并通过自然语言命令帮助开发者更快速地编程。该工具将强大的AI能力与实际开发工作流程无缝集成，支持代码解释、错误修复、Git操作等多种功能。

## 🚀 快速开始

### 系统要求

**支持的操作系统：**
- **macOS**: 10.15+ (Catalina及以上版本)
- **Linux**: Ubuntu 20.04+, Debian 10+
- **Windows**: 仅通过Windows子系统Linux (WSL)支持

**必要前提条件：**
- **Node.js**: 18版本或更高版本
- **npm**: Node包管理器(随Node.js安装)
- **Anthropic账户**: 激活的账户并设置计费方式
- **Git**: 用于版本控制操作

### 安装步骤

```bash
# 全局安装Claude Code
npm install -g @anthropic-ai/claude-code

# 验证安装
claude --version

# 导航到项目目录并启动
cd your-project-directory
claude
```

## 📖 目录

- [安装和设置步骤](#安装和设置步骤)
- [基本使用方法和命令](#基本使用方法和命令)
- [创建和运行demo项目](#创建和运行demo项目)
- [最佳实践和示例](#最佳实践和示例)
- [常见问题和解决方案](#常见问题和解决方案)
- [与其他开发工具的集成](#与其他开发工具的集成)
- [示例演示脚本](#示例演示脚本)
- [成本管理和使用技巧](#成本管理和使用技巧)

---

## 安装和设置步骤

### Windows用户WSL设置

```bash
# 在PowerShell中以管理员身份运行
wsl --install
# 重启计算机并设置Ubuntu
```

### Node.js和npm安装

```bash
# Ubuntu/Debian/WSL用户
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# macOS用户(使用Homebrew)
brew install node

# 验证安装
node --version
npm --version
```

### 配置npm防止权限问题

```bash
# 创建全局包目录
mkdir -p ~/.npm-global

# 配置npm使用新目录
npm config set prefix ~/.npm-global

# 添加到PATH环境变量(添加到~/.bashrc, ~/.zshrc, 或 ~/.profile)
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

### 安装Claude Code

```bash
# 全局安装Claude Code(不要使用sudo)
npm install -g @anthropic-ai/claude-code

# 验证安装
claude --version
```

### 身份验证设置

```bash
# 导航到项目目录
cd your-project-directory

# 启动Claude Code进行首次设置
claude
```

按照OAuth身份验证流程：
1. 完成与Anthropic Console账户的一次性OAuth过程
2. 浏览器窗口会自动打开进行身份验证
3. 登录您的Anthropic账户
4. 复制身份验证代码并粘贴到终端
5. 选择您偏好的终端文本样式

---

## 基本使用方法和命令

### 启动Claude Code

```bash
# 导航到项目目录
cd /path/to/your/project

# 启动交互模式
claude

# 使用特定模型启动
claude --model claude-opus-4

# 继续之前的对话
claude --continue

# 打印模式(非交互式)
claude -p "your prompt here"
```

### 核心命令模式

**询问代码库相关问题：**
```bash
claude
> 我们的身份验证系统是如何工作的？
> 主要的数据模型有哪些？
> 解释一下主要的架构模式
> 总结这个项目的结构
```

**文件操作：**
```bash
> 重构client.py中的代码
> 为这个函数添加文档
> 修复auth模块中的类型错误
> 创建一个用于用户登录的新组件
```

**Git操作：**
```bash
> 提交我的更改
> 创建一个PR
> 在main分支上进行rebase并解决冲突
> 哪个提交添加了markdown的测试？
```

**测试和质量控制：**
```bash
> 运行测试并修复任何失败的测试
> 为登录函数添加单元测试
> 修复这个文件中的代码检查错误
> 优化这个函数的性能
```

### 内置斜杠命令

**项目管理：**
- `/init` - 生成综合项目文档(CLAUDE.md)
- `/clear` - 重置上下文窗口
- `/bug` - 直接向Anthropic报告问题
- `/config` - 修改设置

**高级功能：**
- `/resume` - 从之前的对话中选择
- `/permissions` - 管理命令权限
- `/bash` - 直接执行bash命令

---

## 创建和运行demo项目

### Hello World演示项目

#### 步骤1：创建项目结构
```bash
# 创建新项目目录
mkdir claude-code-hello-world
cd claude-code-hello-world

# 初始化git仓库
git init

# 启动Claude Code
claude
```

#### 步骤2：基本命令尝试
```bash
# 获取项目概览
> 总结这个项目

# 创建简单的Python hello world程序
> 创建一个简单的Python hello world程序

# 创建JavaScript版本
> 创建一个hello world程序并保存为hello.js

# 创建文档
> 创建一个README.md文件来解释这个项目
```

#### 步骤3：高级Hello World示例
```bash
# 创建更复杂的版本
> 创建一个Python程序，每秒打印"Hello World"持续30秒，并在每第5次迭代时打印"Goodbye"

# 重构代码
> 重构hello world程序使其更模块化并添加适当的文档

# 添加错误处理
> 为hello world程序添加错误处理和日志记录
```

### 多文件项目创建

```bash
# 创建Web应用程序演示
> 创建一个简单的Web应用程序，包含HTML、CSS和JavaScript，显示一个问候表单

# 创建Python包结构
> 为计算器库创建Python包结构，包含适当的__init__.py文件和文档

# 创建React组件演示
> 创建一个React组件，显示带有增加和减少按钮的计数器
```

### 实际演示工作流程

#### 1. 代码重构演示
```bash
# 从现有代码开始
> 分析这个代码文件并建议改进

# 应用重构
> 重构这个函数以提高可读性和性能

# 添加文档
> 为这些代码添加全面的文档字符串和注释
```

#### 2. 错误修复演示
```bash
# 识别问题
> 分析这个代码的潜在错误和问题

# 修复特定错误
> 修复这个Python文件中的导入错误

# 运行测试
> 为这个函数创建并运行单元测试
```

#### 3. Git工作流程演示
```bash
# 检查git状态
> 当前的git状态是什么？

# 创建提交
> 用描述性消息提交我的更改

# 创建拉取请求
> 为这个功能创建一个拉取请求

# 解决合并冲突
> 帮助我解决这个合并冲突
```

---

## 最佳实践和示例

### 工作流程最佳实践

#### 研究-计划-实施模式
1. **研究阶段**: 让Claude读取相关文件并理解问题，不编写代码
2. **计划阶段**: 让Claude为解决问题创建详细计划
3. **实施阶段**: Claude在代码中实施解决方案
4. **验证阶段**: 运行测试并验证解决方案正常工作
5. **提交阶段**: 创建提交和拉取请求并添加适当文档

#### 测试驱动开发(TDD)与Claude
```bash
# 首先编写测试
> 基于预期的输入/输出对为这个功能编写测试
> 实现代码使测试通过
> 重构代码保持测试通过
```

#### 扩展思考模式
Claude Code具有特殊的"思考预算"关键字：
- `"think"` - 4,000 tokens
- `"think hard"`, `"megathink"` - 10,000 tokens  
- `"think harder"`, `"ultrathink"` - 31,999 tokens

```bash
> think hard about the best architecture for this microservices system
> ultrathink about optimizing this database query performance
```

### CLAUDE.md最佳实践

在项目根目录创建`CLAUDE.md`文件：

```markdown
# Claude Code项目设置
- **分支命名**: 使用`feature/`, `bugfix/`前缀
- **环境**: 使用pyenv和Python 3.9
- **构建**: `npm run build`
- **测试**: `npm test`
- **代码检查**: `npm run lint && npm run typecheck`
- **注意**: 忽略legacy/auth模块中的废弃警告
```

### 自定义斜杠命令

在`.claude/commands/`目录中存储可重用的提示：

```bash
echo "分析这段代码的性能并建议三个具体的优化方案：" > .claude/commands/optimize.md
echo "查找并修复问题 #$ARGUMENTS" > .claude/commands/fix-issue.md

# 使用方法
/project:optimize
/project:fix-issue 123
```

### 代码质量自动化

```yaml
# .pre-commit-config.yaml示例
repos:
  - repo: local
    hooks:
      - id: lint
        name: Lint code
        entry: npm run lint
        language: system
      - id: test
        name: Run tests
        entry: npm test
        language: system
```

---

## 常见问题和解决方案

### 安装问题

#### npm权限错误
**问题**: 全局npm安装时出现权限错误
**解决方案**:
```bash
mkdir -p ~/.npm-global
npm config set prefix ~/.npm-global
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
npm install -g @anthropic-ai/claude-code
```

#### WSL安装问题
**问题**: OS/平台检测错误，找不到Node错误
**解决方案**:
```bash
# 对于平台检测问题
npm config set os linux
npm install -g @anthropic-ai/claude-code --force --no-os-check

# 对于Node.js路径问题
which npm && which node  # 应该指向/usr/路径，而不是/mnt/c/
# 如果指向Windows，通过Linux包管理器或nvm安装Node
```

### 运行时问题

#### 上下文窗口管理
**问题**: 长对话降低性能
**解决方案**:
```bash
# 在任务之间频繁使用/clear命令
> /clear

# 使用/compact命令总结对话历史
> /compact

# 为不同任务启动新会话以避免上下文污染
```

#### 令牌使用优化
**问题**: 高令牌消耗和成本
**解决方案**:
```bash
# 监控对话大小
/compact  # 总结对话历史

# 为简单任务使用轻量级模型
# 主要模型: Claude 4 (Sonnet/Opus) 用于复杂推理
# Haiku模型: 用于后台任务和简单操作

# 主动重置对话
/clear    # 在主要任务之间清除上下文窗口
```

### 性能问题

#### 大型代码库处理
**问题**: 大型代码库的令牌限制
**解决方案**:
```bash
# 专注于特定目录/模块
> 只分析src/components/目录中的文件

# 使用带有glob模式的目标文件搜索
> 查找所有*.py文件中的身份验证相关代码

# 使用git worktrees创建专注的工作分支
git worktree add ../feature-branch feature-branch
cd ../feature-branch && claude
```

---

## 与其他开发工具的集成

### Visual Studio Code集成

**设置步骤**:
1. 从市场安装Claude Code beta扩展
2. 在VS Code的集成终端中运行`claude`
3. 使用键盘快捷键：
   - `Cmd+Esc` (Mac) / `Ctrl+Esc` (Windows/Linux) 启动Claude

**功能特性**:
- 自动文件上下文共享
- 诊断错误共享(代码检查、语法错误)
- Diff查看器集成用于代码更改
- 选择上下文感知

**配置**:
```bash
# 启用IDE特定功能
/ide  # 在Claude Code中运行此命令连接到IDE

# 在IDE vs终端中配置diff查看
/config
```

### JetBrains IDEs集成

**支持的IDE**: PyCharm, WebStorm, IntelliJ, GoLand

**设置步骤**:
1. 从JetBrains市场安装Claude Code插件
2. 完全重启IDE(如果需要多次)
3. 在内置终端中运行`claude`

**远程开发**: 对于JetBrains远程开发，通过设置 > 插件(主机)在远程主机上安装插件

### GitHub Actions集成

**使用GitHub App设置**:
```bash
# 通过Claude Code安装GitHub app
claude
/install-github-app
```

**手动设置**:
1. 安装Claude GitHub app: https://github.com/apps/claude
2. 将`ANTHROPIC_API_KEY`添加到仓库secrets
3. 复制工作流文件到`.github/workflows/claude.yml`

**示例工作流**:
```yaml
name: Claude Code Review
on:
  pull_request:
    types: [opened, synchronize]
jobs:
  claude-review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: anthropics/claude-code-action@beta
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: "审查这个PR的代码质量和安全问题"
```

### MCP (Model Context Protocol) 集成

**配置方法**:
1. **项目配置**: 项目目录中的`.mcp.json`
2. **全局配置**: 用户级MCP服务器
3. **会话配置**: 临时MCP连接

**示例MCP配置**:
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-filesystem", "/path/to/project"]
    },
    "puppeteer": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-puppeteer"]
    }
  }
}
```

**安装常用MCP服务器**:
```bash
# 安装文件系统访问
claude mcp add filesystem -s user -- npx -y @modelcontextprotocol/server-filesystem ~/Projects

# 安装浏览器自动化
claude mcp add puppeteer -s user -- npx -y @modelcontextprotocol/server-puppeteer

# 安装顺序思考
claude mcp add sequential-thinking -s user -- npx -y @modelcontextprotocol/server-sequential-thinking
```

---

## 示例演示脚本

### 基础介绍演示 (5分钟)
1. 导航到项目目录: `cd demo-project`
2. 启动Claude Code: `claude`
3. 获取概览: `> 总结这个项目`
4. 创建简单函数: `> 创建一个反转字符串的函数`
5. 添加测试: `> 为这个函数创建单元测试`
6. 提交更改: `> 提交这些更改`

### 高级开发演示 (15分钟)
1. 初始化新项目: `> /init`
2. 创建应用程序结构: `> 创建一个FastAPI应用程序结构`
3. 实现功能: `> 创建用户注册和登录端点`
4. 添加数据库集成: `> 添加SQLAlchemy模型和数据库连接`
5. 创建测试: `> 为所有端点创建综合测试`
6. 运行和调试: `> 运行应用程序并测试端点`
7. 部署准备: `> 为这个应用程序创建Dockerfile`

### 代码审查演示 (10分钟)
1. 打开现有代码库: `claude`
2. 分析代码质量: `> 审查这段代码的最佳实践和潜在问题`
3. 重构问题区域: `> 重构已识别的问题`
4. 添加文档: `> 为所有函数添加综合文档`
5. 性能优化: `> 识别并修复性能瓶颈`

---

## 成本管理和使用技巧

### 成本监控
- 使用`/cost`命令监控令牌使用情况
- 使用`/clear`或`/compact`管理上下文大小
- 从较小的代码库开始演示
- 使用具体的提示避免不必要的来回交流

### 订阅选项
- **Claude Pro**: 每月$20 - 包含Claude Code访问权限
- **Claude Max**: 更高的使用限制，可访问Claude Opus 4
- **API直接访问**: 基于使用量的定价(因模型而异)
- **企业版**: Bedrock/Vertex AI集成与现有云计费

---

## 🤝 贡献

欢迎提交问题和改进建议！如果您发现错误或有改进建议，请创建一个issue或提交pull request。

## 📄 许可证

本指南基于MIT许可证开源。

## 📞 支持

- [Anthropic官方文档](https://docs.anthropic.com/en/docs/claude-code/overview)
- [Claude Code GitHub仓库](https://github.com/anthropics/claude-code)
- [Anthropic支持](https://support.anthropic.com)

---

**注意**: Claude Code代表了AI辅助开发的重大进步，将强大的代码库理解和自主任务执行直接带到终端环境中。通过遵循本指南中的最佳实践和工作流程，开发者可以显著提高编程效率，同时保持代码质量和安全性。关键是从简单的用例开始，逐步采用更复杂的功能，并始终保持对AI生成代码的适当审查和测试。