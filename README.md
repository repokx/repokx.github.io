# Repo's Blog

Source code for [repoxu.top](https://repoxu.top), a personal blog built with
[Jekyll](https://jekyllrb.com/) and a customized fork of
[Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy).

## Repository structure

- `_posts`: published articles
- `_drafts`: active drafts
- `_archive`: inactive historical drafts
- `_templates`: reusable writing templates
- `_tabs`: sidebar pages
- `assets`: images, documents, and compiled frontend assets
- `_layouts`, `_includes`, `_sass`, `_javascript`: customized theme source

## Development

Install the Ruby and Node.js dependencies, then run:

```console
bundle exec jekyll serve
npm test
npm run build
```

Pushing to `master` builds and deploys the site through GitHub Pages.
