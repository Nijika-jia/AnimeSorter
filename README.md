<p align="center">
  <img src="https://forthebadge.com/images/badges/made-with-c-sharp.svg" alt="Made with C#">
  <img src="https://forthebadge.com/images/badges/powered-by-responsibility.svg" alt="Powered by Responsibility">
  <img src="https://forthebadge.com/images/badges/built-with-love.svg" alt="Built with Love">
  <img src="https://forthebadge.com/images/badges/open-source.svg" alt="Open Source">
  <img src="https://forthebadge.com/images/badges/it-works-why.svg" alt="It Works Why">
</p>

<h1 align="center">动漫图片分类助手</h1>

<p align="center">
  <b>基于 AnimeTrace API 的动漫角色识别与整理工具</b><br>
  自动识别角色与作品，按规则整理你的动漫图片库。
</p>

<p align="center">
  <a href="https://github.com/Nijika-jia/anime-character-sorter/releases/latest">
    <img src="https://forthebadge.com/images/badges/check-it-out.svg" alt="Check it out">
  </a>
</p>

---

## 下载

### 直接下载
- [最新版本](https://github.com/Nijika-jia/anime-character-sorter/releases/latest)
- [所有版本](https://github.com/Nijika-jia/anime-character-sorter/releases)

### 源码构建
```bash
git clone https://github.com/Nijika-jia/anime-character-sorter.git
cd AnimeSorter
dotnet build AnimeSorterWin\AnimeSorterWin.csproj -c Release
dotnet publish AnimeSorterWin\AnimeSorterWin.csproj -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true
```

---

## 简介

解决动漫图片堆积、角色/作品信息遗忘、手动整理效率低下等问题。

**核心能力：**
- 自动识别动漫角色与对应作品
- 按角色、按作品、按作品+角色多维度分类
- 交互式确认窗口：预览、人脸标注、候选选择、手动修正
- 智能缓存识别结果，避免重复请求
- 导出/导入识别数据，支持离线整理

---

## 功能特点

- **智能缓存系统**：SQLite + MD5，相同图片无需重复识别
- **API 限流控制**：可调并发，内置 429 重试与退避
- **交互式确认窗口**：图片预览、人脸框、候选下拉、手动输入
- **三种分类模式**：按作品 / 按角色 / 按作品+角色
- **文件操作模式**：复制（保留原文件）/ 移动（剪切原文件）
- **数据导出导入**：支持 `.animesortercache.json` 离线整理
- **实时统计面板**：扫描数、缓存命中、识别结果、限流次数
- **现代化界面**：WPF + MaterialDesign，MVVM 架构

---

## 技术栈

| 项目 | 技术 |
|------|------|
| 开发语言 | C# (.NET 8.0) |
| 界面框架 | WPF + MaterialDesignThemes |
| 架构模式 | MVVM (CommunityToolkit.Mvvm) |
| 数据库 | SQLite (Entity Framework Core) |
| 识别服务 | [AnimeTrace API](https://www.animetrace.com/) |
| 核心依赖 | Microsoft.Extensions.DependencyInjection、System.Threading.Tasks.Dataflow |

---

## 使用说明

### 基本流程
1. 启动程序，选择输入目录与输出目录
2. 调整 API 并发数与文件操作模式
3. 点击开始，扫描并识别所有图片
4. 进入确认窗口，查看、选择或修正识别结果
5. 批量确认后，开始整理文件

### 导出与导入
- **导出**：在确认窗口导出当前识别结果为 `.animesortercache.json`
- **导入**：在主界面导入已有数据文件，直接进入确认流程

### 支持格式
JPG、JPEG、PNG、WEBP

### 输出目录结构
```
输出目录/
├── 作品名/
│   └── 角色名/
├── 角色名/
└── Unknown/
```

---

## 注意事项

- 需要联网使用识别功能
- 建议显示器分辨率 1920×1080 及以上
- 缓存数据库路径：`%LocalAppData%\AnimeSorterWin\`

---

## 性能优化

- 异步处理管道：基于 TPL Dataflow
- 流式文件扫描：避免一次性加载大量文件
- 背压控制：防止内存占用过高
- 并发哈希计算：充分利用多核 CPU

---

## 常见问题

1. **无法识别**：检查网络、图片清晰度与文件大小
2. **结果不准**：使用确认窗口手动选择或输入修正
3. **程序无响应**：检查网络与 API 状态，重启程序
4. **API 限流**：降低并发数，减少请求频率

---

## 更新历史

### v2.0.0 - 全新 .NET 版本重构
- 技术栈从 Python 迁移至 .NET 8.0 + WPF
- 新增 SQLite 智能缓存系统
- 新增 API 限流与自动重试机制
- 新增交互式确认窗口
- 新增三种分类模式
- 新增复制/移动文件模式
- 新增数据导出与导入功能
- 新增实时统计面板
- 界面升级为 MaterialDesign 风格

### v1.0.0
- 基础识别与分类功能
- 多模型与双分类模式
- 历史记录与输入补全
- 基础界面与跳过功能

---

## 致谢

本项目基于 [AnimeTrace](https://www.animetrace.com/) API 实现，感谢其提供的精准识别服务。
