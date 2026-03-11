# ForeverMerge 💍

> 一款基于 Astro + Tailwind CSS + GSAP 打造的极简、优雅、高性能的纯前端 H5 婚礼请帖模板。

本项目最初是为了我自己的婚礼而开发。考虑到市面上的 H5 请帖大多需要付费、带有广告，或者加载缓慢，我决定开源这个纯前端的解决方案。它完全由数据驱动，任何人都可以通过简单地替换配置和图片，快速生成属于自己的专属婚礼请帖。

## ✨ 特性

- **⚡️ 极致性能**：基于 Astro 构建，零 React/Vue 运行时开销，纯静态 HTML 输出，秒开体验。
- **🎨 优雅设计**：采用“新中式”红金配色，配合 GSAP 丝滑的滚动视差与入场动画。
- **📱 移动端优先**：完美的 H5 响应式体验，包含音乐自动播放策略、Swiper 照片画廊。
- **⚙️ 数据驱动**：所有文案、时间轴、地图坐标均通过 `src/data/config.json` 集中管理，无需修改代码逻辑。
- **🖼️ 自动化图库**：将婚纱照丢进 `src/assets/gallery/`，Astro 会自动读取、压缩并生成轮播图。
- **🚀 自动化部署**：内置 GitHub Actions 工作流，支持一键推送代码自动构建并部署到兼容 S3 的云存储（如多吉云、阿里云 OSS 等）。

## 🚀 快速开始

### 1. 安装依赖

确保你已安装 Node.js (>=22) 和 pnpm。

```bash
pnpm install
```

### 2. 本地开发预览

```bash
pnpm dev
```

打开浏览器访问 `http://localhost:4321`，建议按 `F12` 切换至手机模式预览。

### 3. 如何替换为你自己的信息？

本模板的设计初衷就是“零代码修改”，你只需要替换素材和配置：

1. **修改文案**：打开 `src/data/config.json`，将里面的新郎新娘名字、日期、酒店地址、时间轴等替换为你自己的。
2. **替换照片**：将你的婚纱照（推荐竖版 3:4 或 9:16 比例）放入 `src/assets/gallery/` 目录下。系统会自动读取该目录下的所有图片生成画廊。
3. **替换视频**：将你们的爱情视频命名为 `main.mp4`，放入 `public/video/` 目录下（建议压缩至 20MB 以内）。
4. **替换音乐**：将背景音乐放入 `public/` 目录，并在 `config.json` 中修改 `music.url` 的路径。

### 4. 构建与部署

如果你想手动构建：

```bash
pnpm build
```

构建产物会生成在 `dist/` 目录下，你可以将其上传到任何静态网站托管服务（如 GitHub Pages, Vercel, 或云厂商的 OSS）。

**自动化部署 (GitHub Actions)**：
本项目内置了 `.github/workflows/deploy.yml`，默认配置了部署到多吉云 (DogeCloud) 的工作流。
你只需要在 GitHub 仓库的 **Settings -> Secrets and variables -> Actions** 中配置以下 2 个环境变量：
- `DOGE_ACCESS_KEY`：你的多吉云 AccessKey
- `DOGE_SECRET_KEY`：你的多吉云 SecretKey
*(可选)* `DOGE_BUCKET_NAME`：如果你有多个存储空间，可以指定部署到哪一个。

配置完成后，每次 `git push` 都会自动获取临时密钥并部署到云存储！

## 📄 目录结构

```text
├── src/
│   ├── assets/
│   │   └── gallery/     # 存放你的婚纱照图片
│   ├── components/      # UI 组件 (封面、画廊、时间轴等)
│   ├── data/
│   │   └── config.json  # 核心配置文件 (修改这里的内容即可)
│   ├── layouts/         # 页面基础布局
│   ├── pages/           # 路由页面
│   └── styles/          # Tailwind 全局样式与主题色
├── public/
│   └── video/           # 存放视频文件 (main.mp4)
└── .github/workflows/   # 自动化部署脚本
```

## 📝 开源协议

本项目基于 **MIT License** 开源。

Copyright (c) 2026 yliu

你可以自由地使用、修改和分发这个模板，无论是用于你自己的婚礼，还是帮朋友制作。祝你们新婚快乐，百年好合！🎉
