# xiaolei.github.io — 个人博客

纯手写静态博客，零依赖、零构建，push 即发布。
中英双语：中文为默认语言（站点根目录），英文在 `en/` 目录下，页面导航可切换。

## 目录结构

```
├── index.html          # 中文主页（文章列表）
├── en/
│   ├── index.html      # 英文主页
│   └── posts/          # 英文文章
├── posts/
│   └── intention.html  # 中文文章（KaTeX 公式）
└── assets/             # 共享图片资源（中英文文章共用）
```

## 本地预览

```bash
cd blog-site
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000
```

## 首次部署（一次性）

1. 在 GitHub 上新建公开仓库，名称必须是 `你的用户名.github.io`
   （例如用户名为 xiaolei，则仓库名为 `xiaolei.github.io`）
2. 推送：

```bash
cd blog-site
git remote add origin git@github.com:你的用户名/你的用户名.github.io.git
git branch -M main
git push -u origin main
```

3. 等 1–2 分钟，打开 `https://你的用户名.github.io` 即可看到博客

> 如果 GitHub 用户名不是 xiaolei，记得把 `index.html` 和 `en/index.html`
> 里的两处 `github.com/xiaolei` 链接替换成你的真实用户名。

## 以后写新文章

1. 复制 `posts/intention.html` 的做法：写 Markdown → 转成 HTML
   （KaTeX CDN + 图片放入 `assets/` 再相对引用），存到 `posts/` 目录
2. 把英文版翻译稿存到 `en/posts/`（保持目录结构一致）
3. 在 `index.html` 和 `en/index.html` 的文章列表顶部各加一张卡片
4. `git add . && git commit -m "new post" && git push`

## 备注

- 公式渲染走 unpkg CDN 的 KaTeX（国内访问比 jsDelivr 稳定），离线打开文章页公式不渲染属正常
- 图片统一放在 `assets/`，WebP 格式压缩后中英文文章共享引用，避免重复内嵌
