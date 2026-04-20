# 环境变量：系统的"快捷方式"配置

## 什么是环境变量

环境变量是操作系统中存储配置信息的"全局变量"，程序运行时可以读取这些值来了解系统环境或用户设置。

**类比理解：**
```
环境变量就像餐厅的"广播系统"
- 系统级广播：所有人（所有程序）都能听到
- 用户级广播：只有特定区域的人能听到

程序通过变量名"调频"来获取信息
```

## 常见环境变量及其作用

| 变量名 | 作用 | 示例 |
|--------|------|------|
| `PATH` | 指定可执行文件的搜索目录 | `C:\Windows;C:\Program Files\Git` |
| `TEMP` / `TMP` | 临时文件存放目录 | `C:\Users\用户名\AppData\Local\Temp` |
| `USERPROFILE` | 当前用户主目录 | `C:\Users\用户名` |
| `APPDATA` | 应用程序数据目录 | `C:\Users\用户名\AppData\Roaming` |
| `SystemRoot` | Windows系统目录 | `C:\Windows` |
| `JAVA_HOME` | JDK安装路径 | `C:\Program Files\Java\jdk1.8.0_301` |
| `PYTHON_HOME` | Python安装路径 | `C:\Python39` |
| `GOPATH` | Go语言工作目录 | `C:\Users\用户名\go` |
| `NODE_PATH` | Node.js模块搜索路径 | `C:\Program Files\nodejs\node_modules` |
| `PATHEXT` | 可执行文件扩展名 | `.COM;.EXE;.BAT;.CMD;.VBS` |

## 查看环境变量

### 方法1：图形界面

**操作步骤：**
1. 右键"此电脑" > "属性"
2. 点击"高级系统设置"
3. 点击"环境变量"按钮
4. 上半部分：用户变量（仅当前用户）
5. 下半部分：系统变量（所有用户）

### 方法2：命令行查看

**查看所有环境变量：**
```cmd
set
```

**查看单个变量：**
```cmd
echo %PATH%
echo %USERPROFILE%
echo %TEMP%
```

**查看系统变量：**
```cmd
# 查看当前会话的PATH
echo %PATH%

# 在PowerShell中查看机器级PATH
[Environment]::GetEnvironmentVariable('Path','Machine')
```

### 方法3：PowerShell
```powershell
# 查看所有变量
Get-ChildItem Env:

# 查看单个变量
$env:PATH
$env:USERPROFILE
```

## PATH变量详解

### PATH的作用
当你在命令行输入一个命令（如 `python`）时，系统会在 PATH 指定的目录中查找对应的可执行文件。

```
输入 python
→ 系统在 C:\Windows\System32 查找
→ 系统在 C:\Python39 查找
→ 系统在 C:\Program Files\Git 查找
→ 找到则执行，找不到则报错"'python' 不是内部或外部命令"
```

### 添加到PATH的典型场景

| 软件 | 图标 | 添加路径 | 原因 |
|------|------|----------|------|
| Git | ![Git](../img/favicon_git.ico) | `C:\Program Files\Git\bin` | 使用 git 命令 |
| Python | ![Python](../img/favicon_python.ico) | `C:\Python39` 和 `C:\Python39\Scripts` | 使用 python/pip 命令 |
| Node.js | ![Node.js](../img/favicon_nodejs.ico) | `C:\Program Files\nodejs` | 使用 node/npm 命令 |
| Java JDK | ![Java](../img/favicon_java.ico) | `C:\Program Files\Java\jdkxxx\bin` | 使用 java/javac 命令 |
| Go | ![Go](../img/favicon_go.ico) | `C:\Go\bin` | 使用 go 命令 |

### 正确添加PATH的方法

**用户变量 PATH（推荐）：**
```
1. 打开环境变量设置
2. 在用户变量中找到 PATH，点击"编辑"
3. 点击"新建"，添加路径
4. 依次点击"确定"保存
```

**注意事项：**
* 路径之间用分号 `;` 分隔
* 不要包含引号
* 避免中文路径
* 新路径放在前面会优先被搜索

### 查看PATH详情
```cmd
echo %PATH%
```
会显示用分号分隔的所有路径列表。

## 临时与永久环境变量

### 临时设置（当前会话有效）
```cmd
set PATH=%PATH%;C:\NewFolder
```
关闭命令行窗口后失效。

### 永久设置（当前用户）
```cmd
setx PATH "%PATH%;C:\NewFolder"
```
**注意**：setx 是永久保存，但当前窗口不会生效，需新开窗口才能使用新值。

### 永久设置（系统级，需管理员权限）

> [!WARNING]
> 系统级环境变量修改会影响所有用户和系统程序。错误修改 PATH 可能导致系统命令无法执行。建议优先使用"用户变量"。

```cmd
setx PATH "%PATH%;C:\NewFolder" /M
```
**注意**：系统级修改需以管理员身份运行命令提示符。

## 常见问题与解决

### 问题1：命令找不到
```
症状：输入 python、git 等命令提示"不是内部或外部命令"
原因：软件安装时未自动添加PATH，或添加失败
解决：
1. 确认软件已正确安装
2. 手动将软件bin目录添加到PATH
3. 重启命令行窗口使设置生效
```

### 问题2：多个版本冲突
```
症状：输入 python 启动的不是想要的版本
原因：PATH中前面的路径优先匹配
解决：
1. 检查 PATH 中各版本的顺序
2. 将想要的版本路径移到前面
3. 或删除不想要的版本路径
```

### 问题3：PATH太长导致问题
```
原因：PATH超过系统限制（Windows 10/11支持更长）
解决：
1. 使用 setx 重新整理PATH
2. 使用短路径别名
3. 清理不再使用的旧路径
```

## 编程开发中的环境变量

### Java开发
```cmd
# 设置JAVA_HOME
setx JAVA_HOME "C:\Program Files\Java\jdk1.8.0_301"

# 将JAVA_HOME\bin添加到PATH
setx PATH "%PATH%;%JAVA_HOME%\bin"
```

### Python开发
```cmd
# 设置PYTHON_HOME
setx PYTHON_HOME "C:\Python39"

# 将Python和Scripts添加到PATH
setx PATH "%PATH%;%PYTHON_HOME%;%PYTHON_HOME%\Scripts"
```

### Node.js开发
```cmd
# Node.js安装后通常自动配置
# 如需手动配置
setx PATH "%PATH%;C:\Program Files\nodejs"
```

### Go开发
```cmd
# 设置GOPATH（工作目录）
setx GOPATH "C:\Users\用户名\go"

# 将go bin添加到PATH
setx PATH "%PATH%;%GOPATH%\bin"
```

## 环境变量最佳实践

1. **用户变量优先于系统变量**
   * 减少对系统的影响
   * 无需管理员权限

2. **PATH顺序很重要**
   * 常用软件放前面
   * 避免多个版本冲突

3. **定期清理**
   * 删除已卸载软件的路径
   * 避免PATH变得臃肿

4. **记录重要配置**
   * 记录重要的环境变量设置
   * 重装系统后可快速恢复

5. **避免中文和特殊字符**
   * 使用英文路径
   * 避免空格（可用短路径绕过）

## 参考资料

| 资源 | 图标 | 链接 |
|------|------|------|
| Microsoft环境变量文档 | ![Microsoft](../img/favicon_edge.ico) | https://docs.microsoft.com/zh-cn/windows/win32/procthread/environment-variables |
| Git官网 | ![Git](../img/favicon_git.ico) | https://git-scm.com/ |
| Python官网 | ![Python](../img/favicon_python.ico) | https://www.python.org/ |
| Node.js官网 | ![Node.js](../img/favicon_nodejs.ico) | https://nodejs.org/ |

> **提示**：修改环境变量后，需要**重启相关程序**（如IDE、终端）才能生效。修改PATH后，重启命令行窗口即可。