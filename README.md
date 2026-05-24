# tanmana-sadhu.github.io

Personal website. Built with Jekyll, deployed via GitHub Pages.

## Quick start — deploy

1. **Create a GitHub repo named exactly `tanmana-sadhu.github.io`** (the repo name must match your username + `.github.io`).
2. From this folder, initialize git and push:
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/tanmana-sadhu/tanmana-sadhu.github.io.git
   git push -u origin main
   ```
3. In the GitHub repo, go to **Settings → Pages**. Set source to `Deploy from a branch` → `main` → `/ (root)` and save.
4. After ~1 minute, the site is live at **https://tanmana-sadhu.github.io**.

That's it — no build step on your end. GitHub Pages builds Jekyll automatically.

## Run locally (optional)

Useful if you want to preview before pushing.

```bash
# One-time setup (needs Ruby 3.x)
gem install bundler
bundle install

# Live preview at http://localhost:4000
bundle exec jekyll serve --livereload
```

On Windows: install Ruby via [RubyInstaller](https://rubyinstaller.org/) (pick a version with DevKit). Open a fresh PowerShell after install, then run the commands above.

## Project structure

```
.
├── _config.yml          Site config (title, author, social links)
├── _data/
│   └── publications.yml Edit this to manage your publication list
├── _includes/           Reusable HTML fragments (nav, footer, head)
├── _layouts/            Page templates
├── _posts/              Blog posts — name as YYYY-MM-DD-slug.md
├── assets/css/main.css  All styling lives here
├── index.md             Home / position page
├── research.md          Research & publications
├── blog.md              Blog index
├── projects.md          Projects
└── interests.md         Personal interests
```

## Common edits

### Add a blog post
Create `_posts/2026-06-01-my-post.md`:
```markdown
---
title: "Post title"
date: 2026-06-01
tags: [llm-agents]
---

Your content here.
```

### Add or edit a publication
Edit `_data/publications.yml` — each entry renders automatically on the Research page.

### Add social links
Edit the `social:` block in `_config.yml`. Empty values are hidden automatically.

### Change the accent color
Edit `--accent` and `--accent-hover` at the top of `assets/css/main.css`.

### Add a profile photo
Drop the image into `assets/img/`, then reference it from `index.md` with `![](/assets/img/your-photo.jpg)`.

## Notes

- The `Gemfile` mirrors GitHub Pages production — what works locally will work after pushing.
- The publication list was seeded from your Google Scholar profile. Citation counts will drift; update them when you feel like it (or just delete the count — it's optional in the data file).
- Empty sections (e.g. on `interests.md`) show a dashed placeholder until you fill them in.
