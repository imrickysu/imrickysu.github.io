# Project Knowledge Map - imrickysu.github.io

## Overview
- **Type:** Jekyll-based blog (GitHub Pages)
- **Language:** Chinese (中文)
- **Theme:** Minimaloid (minimalist)
- **URL:** https://imrickysu.github.io

## Structure
```
├── _posts/           # Blog posts (markdown)
├── _layouts/         # Page layouts
├── _includes/        # Reusable components
├── _config.yml       # Site configuration
├── _drafts/          # Unpublished drafts
├── images/           # Blog images
├── stylesheets/      # CSS
├── javascripts/      # JS
└── index.html        # Homepage
```

## Front Matter Template
```yaml
---
layout: post
title: "标题"
date: YYYY-MM-DD
category: 分类
tags:
  - 标签1
  - 标签2
---
```

## Categories (6 total)
| Category | Count | Usage |
|----------|-------|-------|
| 行旅记 | 25 | Travel logs / 旅行记录 |
| 随想评论 | 15 | Thoughts & opinions / 评论随想 |
| 实践记录 | 13 | Practice records / 实践记录 |
| 方法指南 | 6 | How-to guides / 方法指南 |
| 项目日志 | 2 | Project logs |
| 学习笔记 | 2 | Learning notes |

## Common Tags (Top 15)
| Tag | Count | Notes |
|-----|-------|-------|
| 旅行 | 30 | Travel |
| 效率工具 | 10 | Productivity tools |
| Jekyll | 5 | Blog tech |
| 饮食 | 4 | Food/diet |
| 硬件 | 4 | Hardware |
| 清单 | 4 | Lists |
| 博客 | 4 | Blogging |
| 健康 | 4 | Health |
| 阅读 | 3 | Reading |
| 跑步 | 3 | Running |
| 健身 | 3 | Workout |
| 信息管理 | 3 | Information management |
| iOS | 3 | iOS |
| 阿里云 | 2 | Aliyun |
| 运动 | 2 | Sports |

## Post Naming Convention
- Format: `YYYY-MM-DD-slug.markdown` or `YYYY-MM-DD-slug.md`
- Example: `2026-02-22-jogging-and-surplus.md`

## Image Path
- Images stored in: `/images/`
- Reference in posts: `![](/images/folder/filename.jpg)`

## Workflow
1. Create branch from master
2. Add post to `_posts/`
3. Commit changes
4. Push to origin (orchidsun)
5. Create PR to upstream (imrickysu)

## Config Notes
- Title: 不够折腾
- Email: i@rickysu.com
- Google Analytics: UA-51284079-1
- Markdown: kramdown with GFM input
- Permalink: `/:year/:month/:title`
