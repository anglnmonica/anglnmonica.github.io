---
layout: single
title:  "Build a Technical Writer Portfolio with GitHub Pages and Jekyll"
date:   2026-10-01
---

A portfolio site built with Markdown, Git, and a static site generator
uses the same "docs-as-code" workflow many technical writers already use
for real documentation. Here's how I built mine, including what broke
along the way.

## Prerequisites

- A [GitHub](https://github.com) account
- Git installed (`git --version` to check)
- Ruby 3.0 or later installed (`ruby -v` to check)

## Quick start

1. **Create a repository named `<your-username>.github.io`.**
   This exact naming pattern tells GitHub Pages to publish the site at
   the root of that URL, with no setup required.

2. **Clone it and generate the Jekyll site.**
```bash
   git clone https://github.com/<your-username>/<your-username>.github.io.git
   cd <your-username>.github.io
   gem install jekyll bundler
   jekyll new . --force
```

3. **Preview it locally.**
```bash
   bundle exec jekyll serve
```
   Visit `http://127.0.0.1:4000` to see the default theme running.

4. **Add your own pages.**
   Jekyll turns any `.markdown` file with a few lines of frontmatter
   into a page — no HTML required:
```markdown
   ---
   layout: page
   title: About
   permalink: /about/
   ---
   Your content here.
```

5. **Publish it.**
```bash
   git add .
   git commit -m "Initial site"
   git push
```
   GitHub Pages rebuilds automatically within a minute or two.

## Common issues and how to fix them

**Sass fails to compile on an older macOS.**
Jekyll's default styling engine (Dart Sass) requires a newer macOS than
some machines have. If `jekyll serve` crashes with a Sass error, pin an
older, compatible converter in your `Gemfile`:
```ruby
gem "jekyll-sass-converter", "~> 2.2"
```
Then run `bundle update jekyll-sass-converter`.

**Your homepage shows the wrong content.**
If a static `.html` file and a `.markdown` file both exist for the same
page (for example, a stray `index.html` next to `index.markdown`),
Jekyll may build the static file instead of your real page. Check your
project root for files that don't belong there, and delete them.

**A folder disappears after a Git operation.**
Git doesn't track empty folders. If you delete the last file in a
folder like `_posts`, the folder itself can vanish on your next `git
pull`. Recreate it with `mkdir -p _posts` before adding a new file.

**`_config.yml` throws a cryptic YAML error.**
This file only accepts plain YAML — no Markdown syntax. A stray `**bold**`
or `[link](url)` pasted into it will break the parser with a confusing
message like "did not find expected alphabetic character." Check for
accidentally pasted content if this happens.

## Takeaway

None of these issues were code bugs in the usual sense — they were
environment mismatches, stray files, and a missing folder. That's a
useful reminder for documentation work too: the fix often isn't in what
you wrote, it's in what's sitting around it.