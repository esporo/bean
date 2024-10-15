# Bean

Bean, named after [the best Spore creature](https://spore.fandom.com/wiki/Bean) out there, is a Jekyll theme made to use in both [Esporo](https://esporo.net) and [Simulando](https://simulando.net) fansites. It can be used freely by anyone.

Bean is colorful and customizable. You can change how it looks using CSS variables, you can add widgets to the sidebar or scripts easily.

## Features

- Make it yours with custom colors, typography and backgrounds.
- Automatic light and dark themes!
- Custom sidebar widgets and scripts with includes.
- Support for [pagination](https://github.com/jekyll/jekyll-paginate), [sitemap](https://github.com/jekyll/jekyll-sitemap), [SEO tags](https://github.com/jekyll/jekyll-seo-tag) and [archives](https://github.com/jekyll/jekyll-archives) out of the box.
- Translatable using [theme options](#configuration).

## Installation

### As a remote theme

You can use this theme with the [`jekyll-remote-theme`](https://github.com/benbalter/jekyll-remote-theme) plugin.

On your site repo, run:

```bash
$ bundle add jekyll-remote-theme
```

And add the following to your `_config.yml`:

```yaml
remote_theme: esporo/bean@latest

plugins:
  - jekyll-remote-theme
```

### As a gem-theme

You can also use this theme as a gem-based dependency to your Jekyll site.

Add this line to your Jekyll site's `Gemfile`:

```ruby
gem "bean"
```

And add this line to your Jekyll site's `_config.yml`:

```yaml
theme: bean
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install bean

## Usage

Your theme can be configured using your `_config.yml`. You can also customize the theme, sidebar widgets and site-wide scripts by adding them to your Jekyll setup.

### Configuration

This is an example of a `_config.yml` with all the options available to Bean.

```yaml
title: Your awesome title
description: >-
  Your blog description. It will be shown at the bottom of your website.
tagline: A short-and-sweet tagline.

lang: en
logo: /path/to/your/logo.svg

# Build settings
permalink: "/:year/:month/:day/:title.html"
slug_mode: latin

# Theme Settings
bean:
  show_excerpts: true # this can also be set per-loop page.
  copyright_notice: >-
    Site built using [Bean](https://github.com/esporo/bean).
  date_formats:
    day: "%v"
    month: "%B, %Y"
    year: "%Y"
  translations:
    jump_to_navigation: "Go to navigation"
    jump_to_content: "Go to content"
    archive_date_title: "Posts from %s" # don't forget `%s`, it will be replaced by the date
    archive_tag_title: "Posts with the tag “%s”" # don't forget `%s`, it will be replaced by the tag name.
    archive_category_title: "Posts filed under “%s”" # don't forget `%s`, it will be replaced by the category name.
    post_tagged_with: "Tagged with:"
    blog_pagination_title: "Blog Pagination"
    blog_pagination_next_page: "Older posts"
    blog_pagination_prev_page: "Newer posts"
  
# Menus
main_menu:
  title: Navigate
  items:
    - label: Home
      path: /
    - label: About
      path: /about/
    - label: Bugs?
      path: https://github.com/esporo/bean/issues
    - label: Docs
      path: hhttps://github.com/esporo/bean?tab=readme-ov-file#readme

footer_menu:
  title: Socials
  items:
    - label: Discord
      path: https://discord.gg/
    - label: YouTube
      path: https://youtube.com/
    - label: Facebook
      path: https://www.facebook.com/
```

#### Plugins

Bean adds support for pagination, archives, feeds and SEO tags, so you can configure the settings following these plugins docs:

* [jekyll-paginate](https://jekyllrb.com/docs/pagination/)
* [jekyll-archives](https://github.com/jekyll/jekyll-archives/blob/master/docs/configuration.md)
* [jekyll-feed](https://github.com/jekyll/jekyll-feed?tab=readme-ov-file#usage)
* [jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag/blob/master/docs/usage.md)
* [jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap)

#### Style Options

You can add a `theme.css` in your `/assets/css` directory to customize the style options of your site.

Just copy our [`theme.css`](https://github.com/esporo/bean/blob/main/assets/css/theme.css) and uncomment the lines of the variables you want to change, and you're good to go. Please note that background and color variables have different values for light and dark color schemes.

`theme.css` is also a good place to add custom style rules as well, since it's the last stylesheet called by your theme. It will overwrite any rules set by default.

You can also replace the fonts used in your theme by placing them in your `/assets/fonts` directory and declaring them on `/assets/fonts/fonts.css`.

### Menus

Bean has two menus available. One at the header and other at the bottom of your site. Both are set up in your `_config.yml`:

```yaml
main_menu:
  title: Navigate
  items:
    - label: Home
      path: /
    - label: About
      path: /about/
    - label: Bugs?
      path: https://github.com/esporo/bean/issues
    - label: Docs
      path: hhttps://github.com/esporo/bean?tab=readme-ov-file#readme

footer_menu:
  title: Socials
  items:
    - label: Discord
      path: https://discord.gg/
    - label: YouTube
      path: https://youtube.com/
    - label: GitHub
      path: https://github.com/
```

A menu title is used by screen reader software. It's strongly recommended that you add one to your menus.

### Includes

You can customize parts of the theme by adding includes to your repo.

There are three available includes for you to customize:

* `_includes/below-post.html`: will add content to your post page after the post structure. Useful for comments or notices.
* `_includes/widgets.html`: will add widgets to your blog sidebar. See [Sidebar](#sidebar) below.
* `_includes/scripts.html` will add add site-wide scripts like Disqus and analytics stuff at the end of the `<body>` tag.

### Sidebar

Your blog sidebar can be customized by adding widgets to your `_includes/widgets.html`. The theme provides a default layout for widgets.

You can do something like this:

```html
<!-- Your `_include/widgets.html` -->

{% assign widget_title = "My beautiful widget" %}

{% capture widget_content %}
  <p>This will be shown in my website sidebar! It's useful for a blogroll, useful links, etc.</p>
{% endcapture %}

{% include blog/widget.html title=widget_title content=widget_content %}
```

You can as many widgets as you want, just repeat the process above.

The sidebar can be hidden in a page with the `page` layout. Just add it to your front-matter:

```yml
---
layout: page
title: About
hide_sidebar: true
---
```

### Post authors

Bean tries to bring up post author information from the following sources:

1. An `author` object in the front-matter of your post:
  ```yaml
author:
  name: Will Wright
  url: https://example.com
  ```
2. Your `_data/authors.yml`.
  It may look like this:
  
  ```yaml
will:
  name: Will Wright
  url: https://example.com
  ```
3. A `site.authors` or `site.author` object in your `_config.yml`.
  Something like this will do:
  
  ```yaml
authors:
  will:
    name: Will Wright
    url: https://example.com
  lucy:
    name: Lucy Bradshaw
    url: https://example.net

# or

author:
  name: Will Wright
  url: "https://willwright.blog"
  ```

If none of these sources are available, Bean will just show the value of your `post.author` as it is.



## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/esporo/bean. Be aware that, as this theme is intended to be used by my own fansite, not every suggestion may be applied. You are free to fork it and change it to fit your needs!

## License

The theme is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
