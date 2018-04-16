# narwhal-jekyll-theme

Narwhal is a simple Jekyll theme for a portfolio website. This theme is a fork of [Minima](https://github.com/jekyll/minima), the default Jekyll theme. Much of this Readme is still identical to Minima's, but all sections have been updated to support Narwhal.

[Preview this theme](http://nahrwl.me/narwhal-jekyll-theme/)

![narwhal theme preview](/screenshot.png)

## Installation

Add this line to your Jekyll site's Gemfile:

```ruby
gem "narwhal-jekyll-theme"
```

And add this line to your Jekyll site:

```yaml
theme: narwhal-jekyll-theme
```

And then execute:

    $ bundle


## Contents At-A-Glance

Narwhal has been scaffolded by the `jekyll new-theme` command and therefore has all the necessary files and directories to have a new Jekyll site up and running with zero-configuration.

### Layouts

Refers to files within the `_layouts` directory, that define the markup for your theme.

  - `default.html` &mdash; The base layout that lays the foundation for subsequent layouts. The derived layouts inject their contents into this file at the line that says ` {{ content }} ` and are linked to this file via [FrontMatter](https://jekyllrb.com/docs/frontmatter/) declaration `layout: default`.
  - `home.html` &mdash; The layout for the landing page. Use `portfolio.html` or `post-list.html` for the portfolio landing page and the posts landing page, respectively.
  - `page.html` &mdash; The layout for your documents that contain FrontMatter, but are not posts.
  - `portfolio.html` &mdash; The layout for the portfolio. Renders the list of portfolio items from the `_portfolio` folder. *Add new portfolio items by adding files to the `_portfolio` folder!*
  - `portfolio-page.html` &mdash; The layout for an individual portfolio item.
  - `post.html` &mdash; The layout for your posts.
  - `post-list.html` &mdash; The layout for the blog posts page.

### Includes

Refers to snippets of code within the `_includes` directory that can be inserted in multiple layouts (and another include-file as well) within the same theme-gem.

  - `disqus_comments.html` &mdash; Code to markup disqus comment box.
  - `footer.html` &mdash; Defines the site's footer section.
  - `google-analytics.html` &mdash; Inserts Google Analytics module (active only in production environment).
  - `head.html` &mdash; Code-block that defines the `<head></head>` in *default* layout.
  - `header.html` &mdash; Defines the site's main header section. By default, pages with a defined `title` attribute will have links displayed here.
  - `post-list.html` &mdash; List of all posts.

### Sass

Refers to `.scss` files within the `_sass` directory that define the theme's styles.

  - `narwhal.scss` &mdash; The core file imported by preprocessed `main.scss`, it defines the variable defaults for the theme and also further imports sass partials to supplement itself.
  - `narwhal/_base.scss` &mdash; Resets and defines base styles for various HTML elements.
  - `narwhal/_layout.scss` &mdash; Defines the visual style for various layouts.
  - `narwhal/_syntax-highlighting.scss` &mdash; Defines the styles for syntax-highlighting.

### Assets

Refers to various asset files within the `assets` directory.
Contains the `main.scss` that imports sass files from within the `_sass` directory. This `main.scss` is what gets processed into the theme's main stylesheet `main.css` called by `_layouts/default.html` via `_includes/head.html`.

This directory can include sub-directories to manage assets of similar type, and will be copied over as is, to the final transformed site directory.

### Plugins

Narwhal comes with [`jekyll-seo-tag`](https://github.com/jekyll/jekyll-seo-tag) plugin preinstalled to make sure your website gets the most useful meta tags. See [usage](https://github.com/jekyll/jekyll-seo-tag#usage) to know how to set it up.

## Usage

### Home Layout

`home.html` is a flexible and abstract HTML layout for the site's landing-page. Use `portfolio.html` for the Portfolio landing page and `post-list.html` for the blog / posts page.

#### Biography on a Home Page

To edit the biography paragraph at the top of the landing page(s), refer to the `biography` property in `_config.yml`.

#### Post Listing

The title for the posts list is `Posts` by default and rendered with an `<h2>` tag. You can customize this heading by defining a `list_title` variable in the document's front matter.

--

### Adding Portfolio Items

Add new portfolio items by adding files to the `_portfolio` folder. This is the folder for the portfolio collection, as defined in `_config.yml`.

#### Portfolio Item Front Matter

The front matter for a portfolio item is as follows:

  - `layout` defines the Jekyll layout template. Use `portfolio-page`.
  - `title` Title of the project, which appears on the portfolio home page.
  - `image` URL for the splash image for the project, which appears on the portfolio home page.
  - `importance` An integer. Portfolio items with a higher `importance` number will appear earlier on the portfolio home page. Use this to bump portfolio items to the top of the list.

--

### Customization

To override the default structure and style of Narwhal, simply create the concerned directory at the root of your site, copy the file you wish to customize to that directory, and then edit the file.
e.g., to override the [`_includes/head.html `](_includes/head.html) file to specify a custom style path, create an `_includes` directory, copy `_includes/head.html` from narwhal gem folder to `<yoursite>/_includes` and start editing that file.

The site's default CSS has now moved to a new place within the gem itself, [`assets/main.scss`](assets/main.scss). To **override the default CSS**, the file has to exist at your site source. Do either of the following:
- Create a new instance of `main.scss` at site source.
  - Create a new file `main.scss` at `<your-site>/assets/`
  - Add the frontmatter dashes, and
  - Add `@import "narwhal";`, to `<your-site>/assets/main.scss`
  - Add your custom CSS.
- Download the file from this repo
  - Create  a new file `main.scss` at `<your-site>/assets/`
  - Copy the contents at [assets/main.scss](assets/main.scss) onto the `main.scss` you just created, and edit away!
- Copy directly from Narwhal 2.0 gem
  - Go to your local Narwhal gem installation directory ( run `bundle show narwhal-jekyll-theme` to get the path to it ).
  - Copy the `assets/` folder from there into the root of `<your-site>`
  - Change whatever values you want, inside `<your-site>/assets/main.scss`

--

### Customize navigation links

Right now, customizing the navigation links in the navigation bar is not supported.

--

### Change default date format

You can change the default date format by specifying `site.narwhal.date_format`
in `_config.yml`.

```
# Narwhal date format
# refer to http://shopify.github.io/liquid/filters/date/ if you want to customize this
narwhal:
  date_format: "%b %-d, %Y"
```

--

### Enabling comments (via Disqus)

Optionally, if you have a Disqus account, you can tell Jekyll to use it to show a comments section below each post.

To enable it, add the following lines to your Jekyll site:

```yaml
  disqus:
    shortname: my_disqus_shortname
```

You can find out more about Disqus' shortnames [here](https://help.disqus.com/customer/portal/articles/466208).

Comments are enabled by default and will only appear in production, i.e., `JEKYLL_ENV=production`

If you don't want to display comments for a particular post you can disable them by adding `comments: false` to that post's YAML Front Matter.

--

### Social networks

You can add links to the accounts you have on other sites, with respective icon, by adding one or more of the following options in your config:

```yaml
twitter_username: jekyllrb
github_username:  jekyll
dribbble_username: jekyll
facebook_username: jekyll
flickr_username: jekyll
instagram_username: jekyll
linkedin_username: jekyll
pinterest_username: jekyll
youtube_username: jekyll
googleplus_username: +jekyll
rss: rss

mastodon:
 - username: jekyll
   instance: example.com
 - username: jekyll2
   instance: example.com
```

--

### Enabling Google Analytics

To enable Google Analytics, add the following lines to your Jekyll site:

```yaml
  google_analytics: UA-NNNNNNNN-N
```

Google Analytics will only appear in production, i.e., `JEKYLL_ENV=production`

--

### Enabling Excerpts in the Posts List

To display post-excerpts on posts.html and wherever else posts-list.html is included, simply add the following to your `_config.yml`:

```yaml
show_excerpts: true
```

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/nahrwl/narwhal-jekyll-theme. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## Development

To set up your environment to develop this theme, run `script/bootstrap`.

To test your theme, run `script/server` (or `bundle exec jekyll serve`) and open your browser at `http://localhost:4000`. This starts a Jekyll server using your theme and the contents. As you make modifications, your site will regenerate and you should see the changes in the browser after a refresh.

## Credits

Images used in the demo site are by [JESHOOTS.COM](https://unsplash.com/photos/pUAM5hPaCRI?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText), [Markus Spiske](https://unsplash.com/photos/HDMqSQxjNBE?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText),
[William Iven](https://unsplash.com/photos/gcsNOsPEXfs?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText),
[Hal Gatewood](https://unsplash.com/photos/tZc3vjPCk-Q?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) from [Unsplash](https://unsplash.com/collections/1967508/ux-design?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText).

## License

The theme is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
