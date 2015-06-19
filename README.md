# hugo-memorial-theme
## A theme for websites at Memorial University

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
