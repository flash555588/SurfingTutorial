# XMP：内存超频指南

## 什么是 XMP

**XMP（Extreme Memory Profile）** 是 Intel 制定的内存超频标准，由主板 BIOS 读取和应用预定义的超频配置。

### 通俗理解

- **普通模式**：内存以标准频率运行（如 DDR4-2666）
- **开启 XMP**：自动应用内存官方超频频率（如 DDR4-3600）

### 为什么要开启 XMP

| 对比 | 未开启XMP | 开启XMP |
|------|-----------|---------|
| 频率 | 标准频率 | 更高频率 |
| 性能 | 基础性能 | 提升10-30% |
| 延迟 | 标准延迟 | 更低延迟 |
| 稳定性 | 绝对稳定 | 出厂验证稳定 |

### 前提条件

1. **主板支持**：需要 Intel 100系列及以上主板（或 AMD Ryzen平台的 DOCP/XMP）
2. **内存支持**：购买支持 XMP 的内存条（通常标注 3000/3200/3600 等频率）
3. **双通道建议**：推荐安装 2 条或 4 条内存组建双通道

## 如何开启 XMP

### 步骤一：进入 BIOS

1. 开机时按 **Del** 或 **F2**（不同主板按键不同）
2. 常见按键：
   - 华硕：Del 或 F2
   - 技嘉：Del 或 F2
   - 微星：Del 或 Delete
   - 华擎：Del 或 F2

> **技巧**：开机时屏幕通常会显示 "Press DEL to enter Setup"

### 步骤二：找到 XMP 设置

BIOS 中的位置因主板而异：

```
常见路径：
- OC (超频) > XMP > 选择配置文件
- Advanced (高级) > Memory settings > XMP
- AI Tweaker > XMP
```

### 步骤三：应用 XMP 配置

1. 选择 XMP 配置文件（通常是 Profile 1 或 Profile 2）
2. 保存并退出（通常按 F10）

### BIOS 界面示意

```
┌─────────────────────────────────────┐
│  OC (超频设置)                      │
├─────────────────────────────────────┤
│  CPU Frequency.......... 3200 MHz   │
│  CPU Cache Frequency.... 3200 MHz   │
│  Memory Frequency...... [Auto]     │  ← 当前为自动
│                                     │
│  XMP Configuration                  │
│  > XMP I ........................ [Disabled] │
│                                     │
│  [ 选择 XMP I 后按回车 ]            │
└─────────────────────────────────────┘
```

## 不同品牌主板的 XMP 设置

### 华硕 (ASUS)
```
进入 BIOS > Advanced Mode > AI Tweaker > AI Overclock Tuner > XMP
```

### 技嘉 (GIGABYTE)
```
进入 BIOS > MIT > Advanced Memory Settings > XMP
```

### 微星 (MSI)
```
进入 BIOS > OC > Memory Try It! > XMP
```

### 华擎 (ASRock)
```
进入 BIOS > OC > XMP Configuration > XMP
```

## 常见问题

### Q1：开启 XMP 后无法开机
**解决方法**：
1. 清除 CMOS（拔掉电源，取下主板电池等待5分钟）
2. 逐步尝试：不直接选最高频率的 XMP 配置文件
3. 降低频率：手动设置内存频率为更低值

### Q2：BIOS 中找不到 XMP 选项
**可能原因**：
- 内存不支持 XMP
- BIOS 版本过旧，需要更新
- 主板不支持该内存频率

### Q3：XMP 频率与标注不符
**原因**：XMP 频率需要 CPU 和主板共同支持
- 主板最高支持 2666，但内存是 3600
- 实际运行频率会被限制在主板最高支持频率

## 安全提醒

1. **数据备份**：超频前备份重要数据
2. **逐步尝试**：不要一次性设置过高的频率
3. **温度监控**：运行烤机软件（如 AIDA64）监控温度
4. **压力测试**：使用 MemTest 或 AIDA64 测试稳定性

## 参考资料

| 资源 | 链接 |
|------|------|
| Corsair XMP 指南 | https://www.corsair.com/xmp |
| Kingston XMP | https://www.kingston.com/cn/xmp |
| B 站搜索 | "主板品牌 + XMP 设置" 查找视频教程 |

> **提示**：XMP 是出厂验证的超频设置，正常使用一般不会损坏硬件。但如果频繁蓝屏死机，建议降低频率或关闭 XMP。

---
