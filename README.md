# ICErain · 战术档案

个人站点：游戏理解、版本更新记录、影像。

- **线上地址**：<https://icerain325.com>（Cloudflare 备用：<https://icerain325.pages.dev>）
- **源码仓库**：<https://github.com/ICErain325/ICErain>

## 结构

```
site/
├── index.html          首页：档案 / 战报 / 影像 / 联络
├── 404.html            找不到页面时的兜底
├── favicon.svg         站点图标
├── assets/
│   └── style.css       全站样式（明日方舟 / 罗德岛风格）
└── posts/
    ├── 001.html        示例文章
    └── 002.html        示例文章
```

## 日常更新

```powershell
git add -A
git commit -m "更新内容"
git push
```

推送后 Cloudflare Pages 自动构建，一两分钟生效。构建配置：Build command 留空、Build output directory `/`。

> 如果 `git push` 卡住不动，Ctrl+C 再跑一次。

## 加一篇文章

1. 复制 `posts/001.html`，改名成 `posts/003.html`
2. 改文件里的 `<title>`、`<h1>` 和正文（`<p>` 段落、`<h2>` 小标题）
3. 打开 `index.html`，在「战报」区块里复制一个 `<a class="post">` 块，改标题、摘要、日期和链接

## 换图片

1. 把图片放进 `assets/img/`
2. 在 `index.html` 的影像区块里，把

```html
<div class="tile"><span class="tile-tag">Img</span><span class="tile-label">IMG_01 // 待补充</span></div>
```

换成

```html
<figure class="tile">
  <img src="assets/img/your-photo.jpg" alt="说明">
</figure>
```

## 改社交链接

`index.html` 底部「联络」区块里，把 `href="#"` 换成你的真实主页地址（B站、小红书等）。

## 改主题色

`assets/style.css` 顶部的 `--accent`，默认是 `#ff6a00`（罗德岛橙）。换成别的色值即可。

## 本地预览

用 VS Code 的 Live Server（右键 `index.html` → Open with Live Server），或者：

```powershell
python -m http.server 8080
```

## 部署说明

- 仓库连的是 Cloudflare Pages，`main` 分支即生产环境
- 自定义域名 `icerain325.com` 已绑定，HTTPS 自动签发
- 站点是纯静态文件，可以直接搬到 Vercel / Netlify / 任意服务器