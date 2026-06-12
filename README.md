<p align="center">
  <h1>🧹 Windows 自带磁盘清理：你可能一直在浪费空间</h1>
  <p>
    <img src="https://img.shields.io/badge/Windows-11-0078D4?style=flat-square&logo=windows11" alt="Windows 11">
    <img src="https://img.shields.io/badge/10-23H2-0078D4?style=flat-square&logo=windows" alt="Windows 10">
    <img src="https://img.shields.io/github/stars/web-seeker/windows-disk-cleanup-guide?style=flat-square" alt="Stars">
    <img src="https://img.shields.io/github/license/web-seeker/windows-disk-cleanup-guide?style=flat-square" alt="License">
  </p>
</p>

---

## 为什么这篇指南不一样

网上关于磁盘清理的文章成千上万，但 99% 长这样：

> "打开磁盘清理 → 勾选所有 → 确定。好了。"

**缺少的东西恰好是最关键的：**

| ❌ 大多数文章 | ✅ 这篇指南 |
|---|---|
| 告诉你"全部勾上就行" | **逐项拆解**：每一项是什么、在磁盘哪个位置、清理后有什么后果 |
| 从不提 `sageset` / `sagerun` | **完整 CLI 章节**：从注册表机制到一键脚本 |
| 只知道 cleanmgr | **cleanmgr + Dism** 双引擎，含 `AnalyzeComponentStore` 分析命令 |
| 脚本要你"自己百度" | **三套开箱脚本**：标准版 / 静默版 / 深度版，复制即用 |
| 安全等级模糊 | **⭐ 五级安全评级**，每项清楚标注 "清 / 慎 / 留" |
| 不提清理失败怎么办 | **FAQ 含故障排查**：卡住、空间不涨、清完变慢 |
| 英文为主，中文零散 | **中文原生编写**，命令行注释用中文，可无障碍执行 |

### 一个具体的例子

95% 的用户不知道 **左下角的「清理系统文件」按钮**。不点它，你看到的清理项只能释放几百 MB；点了它，才会出现 Windows 更新缓存（5~30 GB）、Windows.old（10~30 GB）、系统还原点这些真正吃空间的大户。

多数文章不会告诉你这个按钮的原理——它会**重新以管理员权限再扫一次盘**，那些没权限访问的系统备份目录这才被纳入计算。这不是「隐藏功能」，是很多人清完发现 C 盘还是红的根本原因。

---

## 你可以在 1 分钟内判断这篇是否值得读

打开目录扫一眼——如果下面这些你都知道，请关掉并接受我的敬意：

- `cleanmgr /sageset:1` 和 `/sagerun:1` 的区别
- WinSxS 为什么 20 GB 却不能手动删
- `/ResetBase` 什么时候能跑、什么时候不能跑
- `hiberfil.sys` 和 `pagefile.sys` 怎么处理
- 清理后电脑变慢的根因是什么

如果至少有一个不确定——这篇就是写给你的。

---

## 内容结构

```
📋 完整指南 (windows-disk-cleanup-skill.md)
│
├── 🖥️ 界面逐项拆解
│   ├── 标准模式 8 项（普通用户权限可见）
│   ├── 管理员模式 5 项（点击「清理系统文件」后可见）
│   └── 每项的磁盘路径 + 清理后果 + 安全等级
│
├── 🤖 命令行自动化
│   ├── cleanmgr 完整参数表（含 /lowdisk /autoclean）
│   ├── sageset / sagerun 原理与注册表位置
│   └── 三套脚本：标准 → 静默 → 深度
│
├── 🏗️ Dism 组件清理
│   ├── StartComponentCleanup vs ResetBase 区别
│   └── AnalyzeComponentStore 分析命令
│
├── ⚖️ 为什么要用自带工具而不是 CCleaner
├── ❓ FAQ（5 个高频故障场景）
├── 📅 维护日历（周/月/季度/升级后）
└── 📝 附录（路径速查、命令参考卡）
```

---

## 快速开始

### 🚀 第一次使用

```batch
Win + R → 输入 cleanmgr → 回车 → 选 C 盘 → 确定
     ↓
扫描完成后，点击左下角「清理系统文件」← 关键一步
     ↓
勾选所有 → 确定 → 删除文件
```

### 🤖 一键脚本

从 [windows-disk-cleanup-skill.md](./windows-disk-cleanup-skill.md) 的「一键脚本」章节复制任意一套到你电脑，保存为 `.bat`，右键以管理员身份运行。

---

## Star 历史

如果这篇指南帮到了你，⭐ Star 是对它最大的认可：

<p align="center">
  <a href="https://star-history.com/#web-seeker/windows-disk-cleanup-guide&Date">
    <img src="https://api.star-history.com/svg?repos=web-seeker/windows-disk-cleanup-guide&type=Date" alt="Star History Chart">
  </a>
</p>

---

## 贡献

发现错误、有补充的清理项、或想翻译成其他语言——欢迎提 PR。

---

<p align="center">
  <b>维护系统整洁，从每次磁盘清理开始。</b>
</p>
