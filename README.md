# ICErain

个人主页：游戏理解、版本记录、照片。

- **线上地址**：<https://icerain325.com>（Cloudflare 备用：<https://icerain325.pages.dev>）
- **源码仓库**：<https://github.com/ICErain325/ICErain>

## 结构

```
site/
├── index.html          首页：关于 / 文章 / 照片 / 联系
├── 404.html
├── favicon.svg
├── assets/
│   └── style.css       全站样式
└── posts/
    ├── 001.html
    └── 002.html
```

## 日常更新

```powershell
git add -A
git commit -m "更新内容"
git push
```

推送后 Cloudflare Pages 自动构建，一两分钟生效。

> 推送依赖代理。如果 `git push` 卡住，先确认代理开着，再重跑一次。

## 加一篇文章

1. 复制 `posts/001.html`，改名成 `posts/003.html`
2. 改 `<title>`、`<h1>`、`.meta` 里的日期，以及正文
3. 打开 `index.html`，在「文章」列表里复制一条 `<li>`，改日期和链接

## 加照片

1. 图片放进 `assets/img/`
2. 把首页里「照片」那段文字替换成：

```html
<div class="photos">
  <img src="assets/img/photo-01.jpg" alt="说明">
  <img src="assets/img/photo-02.jpg" alt="说明">
</div>
```

照片会自动排成两列（手机上单列）。

## 改主题色

`assets/style.css` 顶部：

```css
--accent: #b45309;   /* 现在是一个偏棕的橙 */
```

## 本地预览

VS Code 装 Live Server 后，右键 `index.html` → Open with Live Server。
或者：

```powershell
python -m http.server 8080
```

## 缓存说明

样式文件带版本号（`style.css?v=5`）。**改完 CSS 要把 HTML 里的版本号 +1**，否则浏览器可能继续用旧样式。

## 部署

- Cloudflare Pages，`main` 分支即生产环境
- Build command 留空，Output directory `/`
- 自定义域名 `icerain325.com` 已绑定，HTTPS 自动签发
- 纯静态文件，可以直接搬到 Vercel / Netlify / 任意服务器