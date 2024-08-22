# Hugo JSON Feed

> Hugo theme component for JSON feed custom Output Format.

This component enables JSON feeds for your site.

## Demo

- [Home Feed](https://lruihao.cn/feed.json)
- [Section Feed](https://lruihao.cn/posts/feed.json)
- [Term Feed](https://lruihao.cn/collections/project/feed.json)

## Install Component

The installation method is the same as [installing a theme](https://fixit.lruihao.cn/documentation/installation/). There are several ways to install, choose one, for example, install through Hugo Modules:

```diff
[module]
  [[module.imports]]
    path = "github.com/hugo-fixit/FixIt"
+ [[module.imports]]
+   path = "github.com/hugo-fixit/hugo-json-feed"
```

## Configuration

Add "jsonfeed" to all the Page Kinds for which you want to create JSON feeds:

```toml
[outputs]
  # <baseURL>/feed.json
  home = ["html", "rss", "jsonfeed"]
  # <baseURL>/posts/feed.json etc.
  section = ["html", "rss", "jsonfeed"]
  # <baseURL>/tags/foo/feed.json etc.
  term = ["html", "rss", "jsonfeed"]
```
