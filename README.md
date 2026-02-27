<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=180&section=header&text=Otaku%20Chart%20Maker&fontSize=42&fontColor=fff&animation=twinkling&fontAlignY=32&desc=把你的本命，收进一张表格里。&descSize=18&descAlignY=52" width="100%" />
</p>

<p align="center">
  <a href="https://github.com/Aytrw/otaku-chart-maker/releases"><img src="https://img.shields.io/github/v/release/Aytrw/otaku-chart-maker?style=flat-square&label=Release&color=e4558b" alt="Release"></a>
  <img src="https://img.shields.io/badge/Go-1.26+-00ADD8?style=flat-square&logo=go&logoColor=white" alt="Go">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-22c55e?style=flat-square" alt="License"></a>
  <a href="https://github.com/Aytrw/otaku-chart-maker"></a>
</p>

<p align="center">
  一张图晒出你的 ACGN 品味 —— 单文件、跨平台、下载即用
</p>

<br>

## ✦ Overview

一个本地运行的 **ACGN 个人喜好表生成器**。从 [Bangumi](https://bgm.tv) / [VNDB](https://vndb.org) 搜索你喜欢的动画、漫画、小说、Galgame，挑选封面填入分类网格，一键导出精美的 PNG 图片 —— 在社交媒体展示你的二次元品味。

> 所有数据 100% 存储在本地，不上传、不追踪、不注册。

<br>

## ✦ Features

- **多数据源搜索** — Bangumi 关键词搜索 + 50+ 题材标签浏览；VNDB 视觉小说搜索
- **四大分类** — 动画 / 漫画 / 小说 / Galgame 一键切换，多标签组合筛选
- **封面编辑** — 内置裁剪、旋转、翻转，支持拖入本地图片
- **PNG 导出** — Canvas 绘制网格布局，像素级还原，一键保存
- **自动持久化** — 每次操作实时写入本地，关闭重开不丢失
- **开箱即用** — 单个二进制文件，无需安装任何运行时，双击启动

<br>

## ✦ Quick Start

### 下载可执行文件（推荐）

前往 [Releases](https://github.com/Aytrw/otaku-chart-maker/releases) 下载对应平台的文件：

| 平台 | 文件 |
|:---|:---|
| Windows | `otaku-chart-maker-windows-amd64.exe` |
| macOS (Apple Silicon) | `otaku-chart-maker-darwin-arm64` |
| Linux | `otaku-chart-maker-linux-amd64` |

```
双击运行 → 浏览器自动打开 http://localhost:8000 → 开始创作
```

### 从源码构建

```bash
git clone https://github.com/Aytrw/otaku-chart-maker.git
cd otaku-chart-maker
go build -o otaku-chart-maker .
./otaku-chart-maker
```

<br>

## ✦ Usage

1. 点击网格中的任意格子，打开封面选择面板
2. 在搜索栏输入作品名称（中 / 日 / 英），或通过标签浏览筛选
3. 点击搜索结果即可下载封面并应用到格子
4. 需要时可使用内置编辑器裁剪封面
5. 全部填好后，点击「保存为图片」导出 PNG

<br>

## ✦ Tech Stack

| 层 | 技术 |
|:---|:---|
| Backend | Go 标准库（`net/http` · `embed`），零第三方依赖 |
| Frontend | 原生 HTML / CSS / JS · Canvas API |
| Data | [Bangumi API](https://bangumi.github.io/api/) · [VNDB API](https://api.vndb.org/kana) |
| Dist | 单二进制，支持 Windows / macOS / Linux |

<br>

## ✦ Project Structure

```
otaku-chart-maker/
├── main.go                  # 入口：embed 前端、启动 HTTP、打开浏览器
├── frontend/
│   └── index.html           # 前端单文件 (HTML + CSS + JS)
├── internal/
│   ├── server/server.go     # 路由、状态读写、封面上传/下载
│   └── api/
│       ├── bangumi.go       # Bangumi 搜索/浏览/封面下载 + 缓存
│       └── vndb.go          # VNDB 视觉小说搜索/封面下载 + 缓存
├── covers/                  # 封面图片（运行时生成）
└── state.json               # 网格状态（运行时生成）
```

<br>

## ✦ Development

```bash
go run .           # 开发模式，前端从磁盘实时读取
go build .         # 构建
```

<br>

## ✦ Roadmap

- [ ] 自定义网格尺寸与分类标签
- [ ] 主题配色切换
- [ ] 拖拽排序格子
- [ ] 高清导出（2x / 3x）
- [ ] GitHub Actions 自动构建发布

<br>

## ✦ License

[MIT](LICENSE) © [Aytrw](https://github.com/Aytrw)

<p align="center">
  <sub>觉得不错？点个 ⭐ 就是对作者最好的应援！</sub>
</p>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer" width="100%" />
</p>
