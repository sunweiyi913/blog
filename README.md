# Ve 的博客

基于 **VS Code + GitHub + Hugo + Cloudflare Pages** 的个人博客，遵循「像写代码一样记笔记」的工作流。

- 静态生成器：[Hugo](https://gohugo.io/) (extended)
- 主题：[PaperMod](https://github.com/adityatelange/hugo-PaperMod)（以 git submodule 方式引入）
- 部署：GitHub Actions → Cloudflare Pages

## 目录结构

```text
.
├── .github/workflows/deploy.yml   # CI：构建 + 部署 Cloudflare Pages
├── archetypes/default.md          # 新建文章的模板
├── content/zh/                    # 中文内容
│   ├── posts/                     # 博客文章
│   ├── about.md                   # 关于页
│   ├── archives.md                # 归档页
│   └── search.md                  # 站内搜索页
├── themes/PaperMod/               # 主题子模块（勿直接修改）
└── hugo.toml                      # 站点配置
```

## 本地开发

```bash
# 新建文章（建议每篇文章一个目录，方便放配图）
hugo new posts/my-post/index.md

# 本地预览：http://localhost:1313
hugo server --buildDrafts --bind 0.0.0.0
```

> 写完后把 front matter 中的 `draft: true` 改为 `false` 才会发布。

## 提交规范（Conventional Commits）

```bash
git commit -m "feat(posts): 添加 K3s 部署笔记"
git commit -m "fix: 修正文章中的链接"
git commit -m "chore: 升级 Hugo 版本"
```

## 首次部署配置（Cloudflare Pages）

1. 在 Cloudflare 控制台创建 Pages 项目，记下 **项目名** 和 **Account ID**，创建 API Token（权限：Account → Cloudflare Pages → Edit）。
2. 在 GitHub 仓库 Settings → Secrets and variables → Actions 中添加：
   - `CLOUDFLARE_API_TOKEN`
   - `CLOUDFLARE_ACCOUNT_ID`
   - `CLOUDFLARE_PAGES_PROJECT`（Pages 项目名）
3. 在 `hugo.toml` 中把 `baseURL` 改为正式域名；在 Pages 项目中绑定自定义域名。

## 更新主题

```bash
git submodule update --remote --merge themes/PaperMod
git commit -am "chore: 升级 PaperMod 主题"
```
