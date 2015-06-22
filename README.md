# hugo-memorial-theme
## A theme for websites at Memorial University

### WARNING

This theme relies on Hugo bug fixes that have not yet been merged to the
mainline tree.
Until [this pull request](https://github.com/spf13/hugo/pull/1216)
is merged, you will need to use
[a patched Hugo](https://github.com/trombonehero/hugo/tree/theme-baseoface).


### Getting started

To get started, clone this repository into your website, e.g.:

```shell
git submodule add https://github.com/musec/hugo-memorial-theme themes/memorial
```

Then create a `layouts/index.ace` file with some content:

```ace
= content main
  p This is my very own content!
```

Then you can run Hugo:

```shell
hugo server --theme=memorial --watch       # for development
hugo --theme=memorial                      # for staging
rsync -avz public/ host:path/to/website/   # deployment
```


### Customization

#### Style

Additional stylesheets can be declared in your site's Hugo config file, e.g.:

```yaml
params:
  extra_style:
    - style/calendar.css
    - style/menu.css
    - style/news.css
```


#### Site hierarchy

To situate your site within a larger hierarchy (e.g., creating a course website
that fits within a larger academic website), create a
`layouts/partials/leftnav.ace` (or HTML, or whatever templating language you
prefer to use with Hugo) with contents such as:

```ace
ul
  {{ $base := .Site.Params.site_base }}

  li
    a href="{{ $base }}/research" Research

  li
    a href="{{ $base }}/teaching" Teaching

    ul
      li
        a href="{{ $base }}/ENGI1000" ENGI 1000

      li
        a href="{{ .Site.BaseURL }}" ENGI 1001
        {{ partial "mun-nav" .Site.Menus.main }}
```
