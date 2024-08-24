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

If your site uses multiple theme components, you need to merge the `outputs` configuration of all theme components. For example, if your site uses both the `FixIt` and `hugo-json-feed` theme components, you need to merge the `outputs` configuration of the two theme components:

```toml
[outputs]
  _merge = "shallow"
  home = ["html", "rss", "jsonfeed", "archives", "offline", "readme", "baidu_urls", "search"]
  page = ["html", "markdown"]
  section = ["html", "rss", "jsonfeed"]
  taxonomy = ["html"]
  term = ["html", "rss", "jsonfeed"]
```

### Parameters

You can set the following parameters in your site configuration file:

```toml
[params]
  # Global Feed config for JSON feed.
  [params.feed]
    # The number of posts to include in the feed. If set to -1, all posts.
    limit = 10
    # whether to show the full text content in feed.
    fullText = true

  # Section page config (all pages in section)
  [params.section]
    # Section feed config for JSON feed.
    [params.section.feed]
      # The number of posts to include in the feed. If set to -1, all posts.
      limit = -1
      # whether to show the full text content in feed.
      fullText = false

  # Term list (category or tag) page config
  [params.list]
    # Term list feed config for JSON feed.
    [params.list.feed]
      # The number of posts to include in the feed. If set to -1, all posts.
      limit = 10
      # whether to show the full text content in feed.
      fullText = true
```

### Front Matter

You can set the following parameters in the front matter of the content file:

```yaml
---
title: "Hello World"
date: 2024-08-24T16:06:33+08:00
hiddenFromFeed: true
feed:
  # feed.limit only invalid in section or term page(_index.md).
  limit: 10
  fullText: true
```
