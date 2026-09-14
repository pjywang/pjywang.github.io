# Junyoung Park's Website

Personal academic website built with Jekyll and the locally customized Minimal Mistakes theme.

## Editing the site

- `_pages/`: homepage, research, software, teaching, Latte's gallery, and the 404 page.
- `_data/navigation.yml`: main navigation links.
- `_config.yml`: site settings and author profile.
- `assets/`: CV, thesis, photos, styles, and JavaScript.

## Local preview

With Ruby and Bundler installed:

```sh
bundle install
bundle exec jekyll serve --host 127.0.0.1
```

Open `http://127.0.0.1:4000/`. Stop the server with Ctrl+C.
For a build without a running server, use `bundle exec jekyll build`.
`_site/`, `.jekyll-cache/`, and `tmp/` are disposable generated output and are ignored by Git.

## Theme files

`_includes/`, `_layouts/`, and `_sass/` contain the theme and local customizations.
`Gemfile` and `minimal-mistakes-jekyll.gemspec` declare the Ruby dependencies.
Keep `LICENSE` for the theme's attribution.

`package.json`, `banner.js`, and the JavaScript sources support rebuilding
`assets/js/main.min.js` with `npm install` followed by `npm run build:js`.
This is only needed when changing the JavaScript, not for routine content edits.

The `jekyll-sitemap` plugin generates `sitemap.xml` automatically.
The two `google*.html` files are search-engine ownership verification files.
