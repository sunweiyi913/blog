---
title: "你好，博客：我的 Hugo 工作流"
date: 2026-09-25T03:00:00+08:00
draft: false
description: "开篇：基于 VS Code + GitHub + Hugo + Cloudflare Pages 的写作工作流"
tags: ["Hugo", "GitHub", "Cloudflare", "工作流"]
categories: ["随笔"]
---

## 为什么开始写博客

试过 Notion、Obsidian 之后，我选择了这套开发者最熟悉的组合：**VS Code + GitHub + Hugo**。

## 这套工作流

1. **VS Code** 写作：Markdown All in One、Front Matter CMS
2. **Git 版本控制**：Conventional Commits 规范提交
3. **Hugo** 生成静态站点：本博客使用 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 主题
4. **GitHub Actions + Cloudflare Pages**：推送 `main` 分支即自动发布

## 日常命令

```bash
# 新建文章
hugo new posts/my-new-post/index.md

# 本地预览（含草稿）
hugo server --buildDrafts --bind 0.0.0.0

# 提交发布
git add .
git commit -m "feat(posts): 我的新文章"
git push
```

推送后大约 1-2 分钟，文章就会自动上线。

> 参考：[像写代码一样记笔记：我的 VS Code + GitHub + Hugo 工作流](https://jimmysong.io/zh/blog/hugo-note-taking/)
