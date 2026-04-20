# CMD 与 PowerShell：命令行基础

## 什么是命令行

命令行是用户与计算机交互的文本界面，通过输入命令来执行操作。相比图形界面，命令行更高效、可以批量处理、适合编写脚本。

**打开方式：**
| 方式 | 图标 | 操作 |
|------|------|------|
| 命令提示符 (CMD) | ![CMD](../img/favicon_edge.ico) | `Win + R` 输入 `cmd` |
| PowerShell | ![PowerShell](../img/favicon_powershell.ico) | `Win + R` 输入 `powershell` |
| Windows Terminal | ![Terminal](../img/favicon_edge.ico) | Microsoft Store 下载，或 `Win + R` 输入 `wt` |
| 管理员权限 | | 右键"命令提示符" > "以管理员身份运行" |

## CMD 基础命令

### 文件和目录操作

| 命令 | 作用 | 示例 |
|------|------|------|
| `cd <路径>` | 切换目录 | `cd C:\Users` |
| `cd ..` | 返回上级目录 | |
| `cd \` | 返回根目录 | |
| `dir` | 列出当前目录文件 | `dir /a` 显示隐藏文件 |
| `mkdir <目录名>` | 创建目录 | `mkdir test` |
| `rmdir <目录名>` | 删除空目录 | `rmdir test` |
| `del <文件名>` | 删除文件 | `del test.txt` |
| `copy <源> <目标>` | 复制文件 | `copy a.txt b.txt` |
| `move <源> <目标>` | 移动/重命名 | `move a.txt C:\test\` |
| `ren <旧名> <新名>` | 重命名 | `ren a.txt b.txt` |
| `type <文件名>` | 显示文件内容 | `type readme.txt` |

### 通配符使用
```
*     代表任意字符（0个或多个）
?     代表单个字符

示例：
dir *.txt          # 列出所有txt文件
del *.tmp          # 删除所有tmp文件
copy a*.txt b\     # 复制所有a开头的txt文件到b目录
```

### 系统信息命令

| 命令 | 作用 |
|------|------|
| `hostname` | 显示计算机名 |
| `whoami` | 显示当前用户名 |
| `ver` | 显示Windows版本 |
| `date` | 显示/设置日期 |
| `time` | 显示/设置时间 |
| `systeminfo` | 显示详细系统信息 |

### 网络命令

| 命令 | 作用 | 示例 |
|------|------|------|
| `ping <地址>` | 测试网络连通性 | `ping www.baidu.com` |
| `ipconfig` | 显示IP配置 | `ipconfig /all` |
| `netstat -an` | 显示网络连接 | |
| `tracert <地址>` | 追踪路由 | |
| `nslookup <域名>` | 查询DNS | |

### 进程和服务命令

| 命令 | 作用 | 示例 |
|------|------|------|
| `tasklist` | 显示所有进程 | |
| `taskkill /pid <PID>` | 结束进程 | |
| `taskkill /im <名称>` | 按名称结束进程 | `taskkill /im chrome.exe` |
| `net start` | 查看已启动服务 | |
| `net stop <服务名>` | 停止服务 | |

### 管道和重定向

```
| (管道)      将前一个命令的输出作为后一个命令的输入
> (重定向)    将输出写入文件（覆盖）
>> (追加)     将输出追加到文件

示例：
dir | more           # 分页显示目录
dir > list.txt      # 将目录列表写入文件
echo hello >> a.txt # 追加hello到文件
```

### 批处理文件

创建 `.bat` 文件可批量执行命令：
```batch
@echo off
REM 这是注释行
echo Starting backup...
copy C:\important\*.doc D:\backup\
echo Backup complete!
pause
```

## PowerShell 基础

PowerShell 是 CMD 的升级版，功能更强大，支持对象管道、脚本编写。

### 基本操作

| 操作 | CMD | PowerShell |
|------|-----|------------|
| 查看当前目录 | `cd` | `Get-Location` 或 `gl` |
| 列出文件 | `dir` 或 `ls` | `Get-ChildItem` 或 `gci` |
| 切换目录 | `cd <路径>` | `Set-Location <路径>` 或 `sl` |
| 查看内容 | `type <文件>` | `Get-Content <文件>` 或 `gc` |
| 复制文件 | `copy <源> <目标>` | `Copy-Item <源> <目标>` 或 `cp` |
| 删除文件 | `del <文件>` | `Remove-Item <文件>` 或 `ri` |
| 创建目录 | `mkdir <目录>` | `New-Item -ItemType Directory <目录>` |

### 别名系统

PowerShell 为常用命令设置了简短别名：

| 别名 | 实际命令 | 作用 |
|------|----------|------|
| `ls` | `Get-ChildItem` | 列出目录 |
| `dir` | `Get-ChildItem` | 列出目录 |
| `cd` | `Set-Location` | 切换目录 |
| `pwd` | `Get-Location` | 显示当前位置 |
| `cp` | `Copy-Item` | 复制 |
| `mv` | `Move-Item` | 移动 |
| `rm` | `Remove-Item` | 删除 |
| `cat` | `Get-Content` | 查看文件 |
| `echo` | `Write-Output` | 输出 |
| `clear` | `Clear-Host` | 清屏 |
| `which` | `Get-Command` | 查找命令位置 |

### PowerShell 特色功能

**1. 对象管道**
```powershell
# CMD方式（文本处理）
dir | findstr ".txt"

# PowerShell方式（对象处理，更强大）
Get-ChildItem | Where-Object {$_.Extension -eq ".txt"}
Get-ChildItem | Where-Object {$_.Length -gt 1MB}
```

**2. 获取帮助**
```powershell
Get-Help Get-ChildItem    # 查看命令帮助
Get-Help Get-Process -Full # 详细帮助
Update-Help               # 更新帮助文档（需管理员）
```

**3. 查看命令来源**
```powershell
Get-Command <命令名>      # 查看命令信息
Get-Alias <别名>          # 查看别名对应的实际命令
```

**4. 对象属性和方法**
```powershell
Get-Process | Get-Member  # 查看对象的属性和方法
(Get-Process)[0].Kill()    # 结束第一个进程
```

### 常用 PowerShell 命令

```powershell
# 进程管理
Get-Process               # 查看所有进程
Stop-Process -Name "chrome"  # 结束chrome进程
Start-Process notepad     # 启动记事本

# 服务管理
Get-Service               # 查看所有服务
Start-Service <服务名>     # 启动服务
Stop-Service <服务名>      # 停止服务

# 网络
Test-Connection <地址>     # ping
Resolve-DnsName <域名>     # DNS查询

# 文件搜索
Get-ChildItem -Recurse -Filter "*.txt"  # 递归搜索所有txt文件
Get-ChildItem -Path C:\ -Include "*.log" -Recurse  # 搜索日志文件

# 系统信息
Get-ComputerInfo          # 详细系统信息
Get-WmiObject Win32_Processor  # CPU信息
Get-WmiObject Win32_DiskDrive # 磁盘信息
```

### PowerShell 脚本

创建 `.ps1` 文件：
```powershell
# 备份脚本示例
$source = "C:\Important"
$dest = "D:\Backup"
$date = Get-Date -Format "yyyy-MM-dd"

# 创建以日期命名的备份文件夹
$backupFolder = "$dest\backup_$date"
New-Item -ItemType Directory -Path $backupFolder -Force

# 复制文件
Copy-Item "$source\*" $backupFolder -Recurse

Write-Host "Backup completed: $backupFolder"
```

**执行策略：**

> [!CAUTION]
> 修改执行策略可能影响系统安全。降低安全等级可能使恶意脚本更容易执行。家庭用户建议仅使用"临时允许"选项。

```powershell
# 查看执行策略
Get-ExecutionPolicy

# 临时允许本地脚本运行（当前会话）
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass

# 永久允许（需管理员）
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

## CMD vs PowerShell 对比

| 特性 | CMD | PowerShell |
|------|-----|------------|
| 学习曲线 | 简单 | 较陡 |
| 命令风格 | 字符串 | 对象 |
| 脚本能力 | 基础批处理 | 完整编程语言 |
| 管道 | 文本流 | 对象流 |
| 系统管理 | 有限 | 强大 |
| 兼容性 | 旧脚本兼容 | 现代化 |

## 选择建议

| 场景 | 推荐 | 图标 |
|------|------|------|
| 简单文件操作 | CMD | ![CMD](../img/favicon_edge.ico) |
| 查看网络状态 | CMD | ![CMD](../img/favicon_edge.ico) |
| 系统管理任务 | PowerShell | ![PowerShell](../img/favicon_powershell.ico) |
| 自动化脚本 | PowerShell | ![PowerShell](../img/favicon_powershell.ico) |
| Windows配置 | PowerShell | ![PowerShell](../img/favicon_powershell.ico) |
| 编程开发 | PowerShell | ![PowerShell](../img/favicon_powershell.ico) |

## 实用技巧

### 1. 命令历史
```
CMD:    按 F7 显示命令历史
PowerShell: 按 F7 或 Up/Down 键浏览历史
```

### 2. 自动补全
```
CMD:    Tab 键补全文件名
PowerShell: Tab 键补全命令、参数、文件名
```

### 3. 快速编辑模式
```
右键点击命令行窗口标题栏 > 属性 > 选项 >
勾选"快速编辑模式"
这样可以用鼠标直接选择和复制文本
```

### 4. 多行输入
```
PowerShell中 Shift+Enter 可以换行继续输入
```

## 参考资料

| 资源 | 图标 | 链接 |
|------|------|------|
| Microsoft CMD文档 | ![Microsoft](../img/favicon_edge.ico) | https://docs.microsoft.com/zh-cn/windows-server/administration/windows-commands/windows-commands |
| PowerShell文档 | ![Microsoft](../img/favicon_powershell.ico) | https://docs.microsoft.com/zh-cn/powershell/ |
| PowerShell Gallery | ![PowerShell](../img/favicon_powershell.ico) | https://www.powershellgallery.com/ |
| Windows Terminal | ![Terminal](../img/favicon_edge.ico) | https://aka.ms/terminal |

> **建议**：学习 PowerShell 的基础知识，它的对象模型和丰富 cmdlet 能大幅提升工作效率。新项目优先使用 PowerShell。