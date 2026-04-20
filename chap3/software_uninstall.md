# 软件卸载：正确清理不需要的程序

## 为什么需要正确卸载

软件卸载不干净会导致各种问题：

* 占着磁盘空间
* 注册表留下一堆垃圾
* 开机启动项越来越多，系统越来越慢
* 可能和别的软件冲突，导致装不上新软件

所以卸载也是个技术活。

## 推荐方法：标准卸载（这些最安全）

### 1. 设置卸载（最推荐）

**操作步骤：**
1. `Win + I` 打开设置
2. 点"应用"
3. 在"已安装的应用"里找要卸载的软件
4. 点右边的"..." > "卸载"
5. 按照提示完成卸载

**优点：** Windows亲儿子，安全可靠

### 2. 控制面板卸载

**操作步骤：**
1. `Win + R` 输入 `appwiz.cpl`
2. 在列表里找要卸载的软件
3. 双击或右键选择"卸载/更改"
4. 按照提示完成卸载

### 3. 软件自带卸载程序

**常见位置：**
* 开始菜单：找"Uninstall"快捷方式
* 安装目录：通常是 `uninst.exe` 或 `Uninstall.exe`
* 软件内：在帮助或设置菜单里找

## 清理残留

### 为什么要清理残留

即使正常卸载了，软件通常还会在一些地方留下痕迹：
* 注册表（少量）
* 用户数据文件夹
* AppData目录

### 方法1：使用专业卸载工具（最推荐）

| 工具 | 特点 | 下载 |
|------|------|------|
| **GeekUninstaller** | 强制卸载、扫描残留 | https://geekuninstaller.com/ |
| **Revo Uninstaller** | 专业卸载、注册表清理 | https://www.revouninstaller.com/ |
| **IObit Uninstaller** | 功能全面、有免费版 | https://www.iobit.com/ |
| **Bulk Crap Uninstaller** | 开源免费、批量卸载 | https://github.com/Klocman/Bulk-Crap-Uninstaller |

**GeekUninstaller 使用方法：**
1. 下载安装 GeekUninstaller
2. 运行后找到要卸载的软件
3. 点"强制卸载"
4. 工具会自动扫描残留并清理

**优点：** 自动搞定残留，不用手动操作

### 方法2：手动清理残留

**操作步骤：**
1. 打开文件资源管理器
2. 地址栏输入 `%appdata%` 回车
3. 删掉软件相关的用户数据文件夹

**常见残留位置：**
| 路径 | 说明 |
|------|------|
| `%appdata%` | C:\Users\用户名\AppData\Roaming |
| `%localappdata%` | C:\Users\用户名\AppData\Local |
| `%programdata%` | C:\ProgramData |

**优点：** 不用装额外软件
**注意：** 删除前确认该软件已经完全卸载了

## 清理启动项

### 禁用开机启动

**方法1：任务管理器（最推荐）**
1. `Ctrl + Shift + Esc` 打开任务管理器
2. 点"启动"标签
3. 禁用不需要的启动项

**方法2：设置**
1. 设置 > 应用 > 启动
2. 关闭不需要的启动项

**方法3：系统配置**
1. `Win + R` 输入 `msconfig`
2. 点"启动"或"启动项"

### 识别启动项

| 启动项 | 建议 | 原因 |
|--------|------|------|
| 杀毒软件 | 保留 | 重要安全软件 |
| 硬件驱动 | 保留 | 键盘、鼠标等 |
| 通讯软件 | 按需 | QQ、微信等 |
| 办公软件 | 按需 | Office等 |
| 未知软件 | 禁用 | 可能是捆绑软件 |

## 高级清理：注册表操作

> [!WARNING]
> 注册表编辑错误可能导致系统无法启动或程序无法运行。优先使用前面的推荐方法。

### 何时需要清理注册表

* 软件卸载后仍有残留项
* 卸载失败需要强制清理
* 其他清理方法无效时

### 清理步骤

1. `Win + R` 输入 `regedit` 回车
2. `Ctrl + F` 搜索软件名
3. 删除相关项（确认无误后再删除）
4. 重点搜索位置：
   * `HKEY_CURRENT_USER\Software`
   * `HKEY_LOCAL_MACHINE\SOFTWARE`

### 安全建议

> [!CAUTION]
> * 删除前务必确认该项与要卸载的软件相关
> * 建议操作前创建系统还原点
> * 不确定的内容不要删除

## 恶意软件清理

### 识别恶意软件特征

* 名称陌生、非英文
* 无法正常卸载
* 卸载后自动重装
* 后台运行、消耗资源

### 强力清理工具

| 工具 | 特点 | 下载 |
|------|------|------|
| **GeekUninstaller** | 强制卸载、扫描残留 | https://geekuninstaller.com/ |
| **Revo Uninstaller** | 专业卸载、注册表清理 | https://www.revouninstaller.com/ |
| **IObit Uninstaller** | 功能全面、有免费版 | https://www.iobit.com/ |
| **Bulk Crap Uninstaller** | 开源免费、批量卸载 | https://github.com/Klocman/Bulk-Crap-Uninstaller |

### 手动清理流程

1. 使用控制面板正常卸载
2. 使用 GeekUninstaller 强制清理残留
3. 使用 Everything 搜索残留文件（按软件名搜）
4. 清理 %appdata% 和 %localappdata% 残留
5. 重启电脑

## 防止软件捆绑

### 安装时注意事项

1. **不要直接点"下一步"**
   * 取消勾选不需要的选项
   * 警惕"推荐软件"勾选框

2. **选择自定义安装**
   * 更改安装路径到D盘
   * 选择性安装组件

3. **使用官网下载**
   * 避免下载站捆绑

### 安装防捆绑技巧

* 使用 Sandboxie 隔离安装
* 使用 VirtualBox 测试新软件
* 安装前先看看用户评论

## 常见问题

| 问题 | 解决方法 |
|------|----------|
| 软件卸载卡住 | 强制结束进程，或使用 GeekUninstaller |
| 卸载后残留 | 使用专业卸载工具清理 |
| 无法卸载 | 进入安全模式卸载 |
| 卸载后仍自启动 | 清理启动项 |
| 卸载报错 | 使用 GeekUninstaller 强制卸载 |

## 良好习惯

### 1. 软件安装管理
* 记录重要软件的安装时间
* 定期检查已安装软件列表
* 卸载不用的软件

### 2. 软件来源管理
* 优先官网下载
* 安装前阅读评论
* 避免下载站

### 3. 定期清理
* 每季度检查一次启动项
* 每半年使用卸载工具深度清理
* 保持软件在最新版本

## 参考资料

| 资源 | 链接 |
|------|------|
| GeekUninstaller | https://geekuninstaller.com/ |
| Revo Uninstaller | https://www.revouninstaller.com/ |
| IObit Uninstaller | https://www.iobit.com/ |
| Bulk Crap Uninstaller | https://github.com/Klocman/Bulk-Crap-Uninstaller |

> **建议**：软件在精不在多，定期清理不用的软件，保持系统干净整洁。优先使用推荐方法，注册表清理请谨慎。