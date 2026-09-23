# Ziyi Xie 的个人主页

网站：<https://zoeabcd.github.io>。使用 Jekyll 生成静态网页，由 GitHub Pages 发布。以下路径和命令均相对于这个 README 所在目录。

## 日常维护

| 想修改的内容 | 编辑位置 |
| --- | --- |
| 首页 About Me 正文 | `_pages/about.md` |
| 侧栏姓名、简介、邮箱、学术链接 | `_config.yml` 的 `author` |
| 头像 | 替换 `images/my_pic.jpg`；使用其他文件名时同步更新 `author.avatar` |
| 顶部菜单名称、顺序、链接 | `_data/navigation.yml` |
| 论文 | `_publications/`，每篇一个 Markdown 文件 |
| 博客 | `_posts/`，每篇一个 `YYYY-MM-DD-short-title.md` 文件 |
| 报告与教学 | `_talks/`、`_teaching/` |
| 图片与 PDF 等附件 | `images/`、`files/` |

文件开头一对 `---` 之间是页面设置（front matter），其后是 Markdown 正文。已有页面的 `permalink` 决定访问网址，修改内容时保留它；已有附件的文件名和路径也应保留，避免论文、博客和外部引用失效。

## 新增论文与博客

在 `_publications/` 新建 `YYYY-MM-DD-short-title.md`，例如：

```yaml
---
title: "论文标题"
collection: publications
category: preprints
permalink: /publication/2026-09-22-short-title
date: 2026-09-22
venue: 'arXiv 预印本'
authors:
  - 合作者姓名
  - Ziyi Xie
links:
  - label: PDF
    url: https://example.com/paper.pdf
  - label: arXiv
    url: https://arxiv.org/abs/论文编号
---
```

把示例内容替换成论文信息。`category` 只使用 `preprints`（预印本与技术报告）或 `published`（正式发表）。`authors` 按论文的完整作者顺序填写，`Ziyi Xie` 会自动加粗；`venue` 填会议、期刊或预印本编号。`links` 按需要添加 PDF、arXiv、Publisher 或 ECCC 链接。

论文列表按分组、日期倒序自动收录。预印本正式发表后更新同一个文件的 `category`、`date`、`venue` 和链接，保留原有 `permalink`，无需为不同版本重复添加条目。

在 `_posts/` 新建 `YYYY-MM-DD-short-title.md`，例如：

```yaml
---
title: "文章标题"
date: 2026-09-22 12:00:00 +0800
permalink: /blog/short-title/
excerpt: "一两句话的摘要。"
tags:
  - quantum cryptography
---
```

在 front matter 结束的 `---` 后写正文，博客归档会自动收录。附件放入 `files/`，可用 `[附件说明](/files/文件名.pdf)` 链接。现有博客所引用的证明文件和时间戳文件需一并保留。

## 新增助教经历

在 `_teaching/` 新建文件，例如 `2026-spring-itcs.md`：

```yaml
---
title: "Introduction to Theoretical Computer Science"
collection: teaching
permalink: /teaching/2026-spring-itcs/
semester: "Spring 2026"
instructor: "Zhengfeng Ji"
venue: "Tsinghua University, DCST"
role: "Teaching Assistant"
date: 2026-01-01 # 仅用于学期排序，不表示具体开课日期。
course_url: https://itcs.finite-dimensional.space/
---
```

列表显示学期、教师与助教身份，按学期倒序排列；同学期按课程标题降序排列。没有课程网站时省略 `course_url`，标题会显示为普通文本。外部课程网址放在 `course_url`，`permalink` 只填写站内路径。

## 本地预览与检查

先准备 Ruby 和 Bundler，在本目录运行：

```bash
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll serve --livereload --host localhost
```

打开 <http://localhost:4000>。内容修改会自动重新构建；修改 `_config.yml` 后需要停止并重新启动预览。仅构建而不启动预览时运行 `bundle exec jekyll build`。

提交前查看首页、论文、Talks、Teaching、博客和 Sitemap，确认附件链接、公式、手机菜单与深浅色切换正常。`_site/` 是生成结果，不要直接编辑。

也保留了 Docker 与 VS Code Dev Container：安装 Docker 后可运行 `docker compose up --build`，或在 VS Code 中选择 **Dev Containers: Reopen in Container**，同样访问端口 4000。

日常改文字不需要 npm。只有修改 `assets/js/_main.js` 或导航插件等 JavaScript 源码时，才运行 `npm install` 和 `npm run build:js` 更新 `assets/js/main.min.js`。`_layouts/`、`_includes/`、`_sass/` 管理布局、共用部件和样式；`markdown_generator/` 是保留的旧版批量生成工具，输出需按本文示例调整字段，平时直接编辑 Markdown 即可。

## 发布

将修改提交并推送到 GitHub 仓库的 `master` 分支后，`.github/workflows/pages.yml` 会自动构建并部署。可在 GitHub 的 **Actions** 中查看 “Deploy personal site to Pages” 的结果，也可手动运行该工作流；成功后访问网站检查更新。

## 模板来源

基于 [Academic Pages](https://github.com/academicpages/academicpages.github.io)，其源自 Michael Rose 的 [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes)。保留原模板的 [MIT 许可证](LICENSE) 与版权声明。
