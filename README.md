# stevehoang

Portfolio and blog of Hoang Pham-Van, built with Jekyll and served by GitHub Pages at
<https://phamvanhoang9.github.io/stevehoang/>. Pushing to `main` rebuilds the site; there is no CI step.

Theme: [Massively](https://html5up.net/massively) by HTML5 UP (CCA 3.0, see `LICENSE.txt`).

## Layout

| Path | What it is |
|---|---|
| `_config.yml` | Site settings, social links, script list, the `blog_min_posts` threshold |
| `_layouts/default.html` | Shared page shell: head, header, nav, footer, scripts |
| `_layouts/post.html` | A single blog post |
| `_includes/` | Small shared snippets (post date, tag buttons) |
| `index.html` | Projects page (home) |
| `blog/index.html` | Blog listing: newest post featured, the rest in a grid |
| `blog/tags/index.html` | Every tag with its posts; tag buttons link here as `/blog/tags/#<tag>` |
| `_posts/` | Published posts |
| `_drafts/` | Unpublished posts; never built on GitHub Pages |
| `assets/sass/` | SASS source. `assets/css/main.css` is the compiled output; edit both together |

## Writing a post

Create `_posts/YYYY-MM-DD-short-title.md`:

```markdown
---
title: Why ATLAS rebuilds its own citations
description: One or two sentences shown on the blog listing and in search results.
tags: [engineering, rag, atlas]
image: /images/some-image.jpg      # optional
image_alt: What the image shows    # required if image is set
---
Post body in Markdown.
```

- Tags are free-form and a post can carry any number of them. Use lowercase, and reuse existing tags
  where they fit so the tags page stays useful.
- The URL becomes `/blog/YYYY/MM/short-title/`.
- Work in progress goes in `_drafts/` without the date prefix.
- The **Blog** link in the nav stays hidden until `blog_min_posts` (3) posts are published. The pages
  themselves exist at `/blog/` either way.
- An RSS feed is generated at `/blog/feed.xml`.

## Local preview

Ruby is not required; the preview runs in Docker with the same gem set GitHub Pages uses:

```bash
docker run --rm -it -p 4000:4000 -v "$PWD:/srv/jekyll" -w /srv/jekyll ruby:3.3 sh -c "bundle install && bundle exec jekyll serve --host 0.0.0.0 --drafts --baseurl /stevehoang"
```

Then open <http://localhost:4000/stevehoang/>. Drop `--drafts` to see exactly what will be published.
