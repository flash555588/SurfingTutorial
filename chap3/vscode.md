# VS Code 使用指南：程序员的第一代码编辑器

## 什么是 VS Code

**Visual Studio Code（简称 VS Code）** 是微软开发的免费开源代码编辑器，支持 Windows、macOS、Linux 系统。

**为什么选择 VS Code：**
* 免费开源，不用破解
* 启动快，占用少
* 插件贼多，想装啥装啥
* 代码补全智能（IntelliSense）
* 内置 Git 版本控制
* 调试功能强大

**官网**：https://code.visualstudio.com/

## 安装与配置

### 安装

1. 访问 https://code.visualstudio.com/Download
2. 下载 Windows 版本安装包
3. 安装时建议勾选：
   * "添加到 PATH"
   * "通过 Code 打开"右键菜单

### 主题设置

```
路径：Ctrl + K, Ctrl + T
内置主题：Dark+、Light+
其他主题：可在插件市场搜索安装
```

### 字体设置

```json
// 设置 > 编辑器 > 字体
"editor.fontFamily": "Cascadia Code, Consolas, monospace",
"editor.fontSize": 14,
"editor.lineHeight": 1.6,
"editor.fontLigatures": true
```

## 核心快捷键

### 文件操作

| 快捷键 | 功能 |
|--------|------|
| `Ctrl + N` | 新建文件 |
| `Ctrl + O` | 打开文件 |
| `Ctrl + S` | 保存 |
| `Ctrl + Shift + S` | 另存为 |
| `Ctrl + W` | 关闭文件 |
| `Ctrl + K S` | 保存所有 |

### 编辑操作

| 快捷键 | 功能 |
|--------|------|
| `Ctrl + X` | 剪切行 |
| `Ctrl + C` | 复制行 |
| `Ctrl + V` | 粘贴 |
| `Ctrl + Z` | 撤销 |
| `Ctrl + Y` | 重做 |
| `Ctrl + /` | 注释/取消注释 |
| `Shift + Alt + A` | 块注释 |
| `Ctrl + D` | 选中下一个相同词 |
| `Ctrl + Shift + L` | 选中所有相同词 |
| `Alt + ↑/↓` | 移动行 |
| `Shift + Alt + ↑/↓` | 复制行 |

### 搜索与替换

| 快捷键 | 功能 |
|--------|------|
| `Ctrl + F` | 查找 |
| `Ctrl + H` | 替换 |
| `Ctrl + Shift + F` | 全局搜索 |
| `Ctrl + Shift + H` | 全局替换 |
| `F3` | 查找下一个 |
| `Shift + F3` | 查找上一个 |

### 导航操作

| 快捷键 | 功能 |
|--------|------|
| `Ctrl + P` | 快速打开文件 |
| `Ctrl + G` | 跳转到行号 |
| `Ctrl + Shift + O` | 跳转到符号 |
| `F12` | 跳转到定义 |
| `Alt + F12` | peek 定义 |
| `Ctrl + Tab` | 切换标签页 |
| `Ctrl + B` | 显示/隐藏侧边栏 |

### 多光标编辑

| 快捷键 | 功能 |
|--------|------|
| `Alt + Click` | 添加光标 |
| `Ctrl + Alt + ↑/↓` | 上下添加光标 |
| `Ctrl + U` | 撤销上一个光标 |
| `Ctrl + Shift + i` | 在行尾添加光标 |

### 终端

| 快捷键 | 功能 |
|--------|------|
| `` Ctrl + ` `` | 打开/关闭终端 |
| `` Ctrl + Shift + ` `` | 新建终端 |
| `Ctrl + Shift + 5` | 拆分终端 |

## 必备插件推荐

### 通用插件

| 插件名称 | 功能 |
|----------|------|
| **Chinese (Simplified)** | 中文语言包 |
| **Material Theme** | 主题美化 |
| **Prettier** | 代码格式化 |
| **ESLint** | JS 代码检查 |
| **Bracket Pair Colorizer** | 括号高亮 |
| **GitLens** | Git 增强 |
| **Settings Sync** | 配置同步 |

### 语言支持

| 插件名称 | 支持语言 |
|----------|----------|
| **Python** | Python |
| **C/C++** | C/C++ |
| **Java Extension Pack** | Java |
| **Go** | Go 语言 |
| **Rust Analyzer** | Rust |
| **Vetur** | Vue.js |
| **ES7+ React/Redux/React-Native** | React |

### 前端开发

| 插件名称 | 功能 |
|----------|------|
| **Live Server** | 本地开发服务器 |
| **Auto Rename Tag** | 自动重命名标签 |
| **CSS Peek** | CSS 定义跳转 |
| **HTML CSS Support** | CSS 提示 |
| **Tailwind CSS IntelliSense** | Tailwind 提示 |

### 效率工具

| 插件名称 | 功能 |
|----------|------|
| **Git History** | 可视化 Git 历史 |
| **Docker** | Docker 支持 |
| **REST Client** | HTTP 请求测试 |
| **Markdown Preview Enhanced** | Markdown 预览 |

## 常用设置

### 用户设置 (settings.json)

```json
{
  // 编辑器
  "editor.fontSize": 14,
  "editor.tabSize": 2,
  "editor.wordWrap": "on",
  "editor.formatOnSave": true,
  "editor.minimap.enabled": false,

  // 主题（根据个人喜好选择）
  "workbench.colorTheme": "Dark+",

  // 终端
  "terminal.integrated.fontSize": 13,
  "terminal.integrated.defaultProfile.windows": "PowerShell",
  "terminal.integrated.profiles.windows": {
    "PowerShell": {
      "source": "PowerShell"
    }
  },

  // 文件
  "files.autoSave": "afterDelay",
  "files.exclude": {
    "**/.git": true,
    "**/node_modules": true
  },

  // 搜索
  "search.exclude": {
    "**/node_modules": true,
    "**/dist": true
  }
}
```

### 工作区设置

在项目根目录创建 `.vscode/settings.json` 可设置项目专用配置。

## Git 集成

### 图形化操作

1. 点击左侧源代码管理图标（或 `Ctrl + Shift + G`）
2. 显示所有更改的文件
3. 点击文件查看具体更改
4. 输入提交信息，点击提交

### 常用操作

| 操作 | 位置 |
|------|------|
| 提交 | 源代码管理 > √ 按钮 |
| 推送 | 源代码管理 > ... > 推送 |
| 拉取 | 源代码管理 > ... > 拉取 |
| 切换分支 | 左下角分支图标 |
| 查看历史 | 源代码管理 > 提交历史 |

### GitLens 增强功能

* 每行代码显示最后修改人和时间
* 点击可查看完整 commit 历史
* 强大的比较视图

## 调试功能

### 设置断点

1. 点击代码行号左侧设置断点
2. 按 `F5` 开始调试
3. 使用调试工具栏控制执行

### 调试工具栏

| 按钮 | 快捷键 | 功能 |
|------|--------|------|
| ▶️ | `F5` | 开始/继续 |
| ⏸️ | `F6` | 暂停 |
| ⏹️ | `Shift + F5` | 停止 |
| ↩️ | `Shift + F11` | 跳出 |
| ⤵️ | `F10` | 单步跳过 |
| ⤵️ | `F11` | 单步进入 |

### 调试控制台

* **调试控制台**：`Ctrl + Shift + Y`
* 查看变量值
* 执行表达式

## 集成终端

### 基本操作

```bash
# 打开终端
Ctrl + `

# 新建终端
Ctrl + Shift + `

# 拆分终端
Ctrl + Shift + 5

# 切换终端
Ctrl + PageUp / PageDown
```

### 常用终端命令

```bash
# 运行 Python
python app.py

# 运行 Node.js
node app.js

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

## 实用技巧

### 1. 命令面板

```
Ctrl + Shift + P
```
输入命令名称搜索执行，支持模糊匹配。

### 2. 快速生成代码

```
输入 html:5 + Tab → 生成 HTML5 模板
输入 ! + Tab → 同上
输入 div + Tab → 生成 <div></div>
输入 lorem + Tab → 生成随机文本
```

### 3. 代码片段（Snippets）

创建自定义代码片段：
1. `Ctrl + Shift + P` > "配置用户代码片段"
2. 选择语言（如 global, python, javascript）
3. 编写 snippet：

```json
{
  "console.log": {
    "prefix": "clg",
    "body": "console.log($1);",
    "description": "console.log"
  }
}
```

### 4. 多点编辑

* `Ctrl + Shift + L` 选中所有相同词
* `Ctrl + F2` 选中所有相同词并进入编辑
* `Alt + Click` 添加多个光标

### 5. 代码格式化

```bash
# 格式化整个文件
Shift + Alt + F

# 格式化选中内容
Ctrl + K Ctrl + F
```

## 常见问题

### Q1：VS Code 字体发虚
**解决**：启用字体平滑
```json
"editor.fontSmoothing": "antialiased"
```

### Q2：终端中文显示乱码
**解决**：在终端软件中设置编码为 UTF-8

CMD 设置：
```cmd
chcp 65001
```

PowerShell/Windows Terminal 通常默认 UTF-8，无需额外设置。

### Q3：Git 中文文件名乱码
**解决**：在终端设置
```bash
git config --global core.quotepath false
```

### Q4：插件安装失败
**解决**：
* 检查网络连接
* 尝试设置代理
* 重启 VS Code

## 参考资源

| 资源 | 链接 |
|------|------|
| VS Code 官网 | https://code.visualstudio.com/ |
| 官方文档 | https://code.visualstudio.com/docs |
| 快捷键速查 | https://code.visualstudio.com/shortcuts |
| 插件市场 | https://marketplace.visualstudio.com/ |
| VS Code Rocks | https://vscodered.xyz/ |

> **提示**：VS Code 功能丰富，不需要一次学会所有。先掌握基础操作和几个必备插件，其他功能在需要时再学习即可。