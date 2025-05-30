# MCP GitHub服务器"No tools available"问题解决指南

## 问题描述
在Cursor中配置GitHub MCP服务器后显示"No tools available"，无法使用GitHub相关的工具。

## 解决方案

### 1. 推荐方案：使用npx配置（已实施）

您的配置文件已更新为：
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-github@latest"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your_token_here"
      }
    }
  }
}
```

**操作步骤：**
1. 完全关闭Cursor
2. 重新启动Cursor
3. 等待5-10秒让服务器初始化
4. 检查GitHub工具是否可用

### 2. 常见问题排查

#### 问题1：npx命令不存在
确保已安装Node.js和npm：
```bash
# 检查Node.js版本
node --version
npm --version

# 如果没有安装，使用Homebrew安装
brew install node
```

#### 问题2：GitHub Token权限不足
确保Token具有以下权限：
- `repo` (仓库访问)
- `read:org` (读取组织信息)
- `read:user` (读取用户信息)

#### 问题3：网络连接问题
检查是否可以访问GitHub API

#### 问题4：Cursor日志检查
1. 打开Cursor
2. 按 `Cmd+Shift+P` (macOS) 或 `Ctrl+Shift+P` (Windows/Linux)
3. 搜索并选择 "Developer: Toggle Developer Tools"
4. 查看Console选项卡中的错误信息

### 3. 验证工具是否工作

成功配置后，您应该能看到以下GitHub工具：
- `create_repository` - 创建新的GitHub仓库
- `create_issue` - 创建问题
- `get_file_contents` - 获取文件内容
- `create_pull_request` - 创建拉取请求
- `search_repositories` - 搜索仓库
- `fork_repository` - 分叉仓库

## 联系支持

如果问题仍然存在，请：
1. 检查Cursor开发者工具中的错误日志
2. 确认GitHub Token权限
3. 尝试不同的配置方案
4. 考虑更新Cursor到最新版本