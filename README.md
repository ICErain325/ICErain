# 阿岚的小站

一个零依赖的静态站点：纯 HTML + CSS，没有构建步骤，没有框架，整个目录丢给任何静态托管都能跑。

## 本地预览

在 `site` 目录下执行：

```powershell
python -m http.server 8080
```

然后浏览器打开 <http://localhost:8080>。

## 改成你自己的

1. 全局搜索「阿岚」，换成你的名字（`index.html`、`about.html`、`posts/*.html` 和页脚都要改）。
2. 改每个页面 `<head>` 里的 `<title>` 和 `<meta name="description">`。
3. 配色在 `assets/style.css` 顶部的 `:root` 里，改 `--accent` 一个变量就能换主题色。
4. 加文章：复制 `posts/hello.html` 改名，改标题和正文，再到 `index.html` 的文章列表里加一条 `<li>`。
5. 头像是 `favicon.svg`，直接替换内容即可。

## 部署到 Cloudflare Pages（免费）

### 方式一：连 GitHub（推荐）

之后每次 `git push` 都会自动重新发布。

1. 在 GitHub 新建一个仓库，比如 `mysite`（不要勾选初始化 README）。
2. 在 `site` 目录执行：

```powershell
git init
git add .
git commit -m "init site"
git branch -M main
git remote add origin https://github.com/<你的用户名>/mysite.git
git push -u origin main
```

3. 打开 Cloudflare Dashboard → Workers & Pages → Create → Pages → Connect to Git，选这个仓库。
4. 构建命令留空，输出目录填 `/`，点 Save and Deploy。
5. 拿到一个 `xxx.pages.dev` 的免费地址。

### 方式二：命令行直接上传（不用 GitHub）

```powershell
npx wrangler pages deploy . --project-name=mysite
```

## 绑定自己的域名

1. 买域名（Cloudflare、阿里云、腾讯云都行）。
2. Cloudflare Pages 项目 → Custom domains → 添加域名，按提示把 DNS 指过去。
3. HTTPS 证书自动签发，不用手动配置。

## 关于备案

服务器在中国大陆才需要 ICP 备案。Cloudflare Pages 用的是海外节点，不需要备案，但国内访问速度因地区而异。如果要国内访问快，就得用国内云服务器 + 备案。

## 换别的托管

这里没有任何平台专属配置。同一个目录可以直接放 Vercel、Netlify、GitHub Pages，或者任意一台装了 nginx 的服务器。