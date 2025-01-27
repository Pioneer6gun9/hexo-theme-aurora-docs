# Getting started

## Prerequisites

- [Hexo 6.3+](https://hexo.io/)
- [Yarn](https://classic.yarnpkg.com/en/) or [NPM](https://docs.npmjs.com/getting-started) installed

---

## Upgrade from v1.x to v2.x

Since all the hexo script and generators had being moved to a separate Hexo plugin package ([hexo-plugin-aurora](https://github.com/auroral-ui/hexo-plugin-aurora)). Therefore the way we install `Hexo Aurora Theme` had changed since v2.x.

If you are a brand new user of this theme, just follow the Installation guide below.

If you are upgrading from v1.x to v2.x, please follow the [v2.x upgrade guide](/guide/upgrade.html#v1-x-to-v2-x-upgrade)

---

## Installation

This section will help you install the theme on an existing Hexo Blog project.

---

### Step 1 - Installing theme package

> **In your console, go to the root directory of your Hexo project, then run the following command to install the theme:**

:::warning
For version 2.0+, the generator scripts are all moved to `hexo-plugin-aurora` package. You need to install this package to use this theme!
:::

<CodeGroup>
  <CodeGroupItem title="YARN">

```shell:no-line-numbers
yarn add hexo-theme-aurora hexo-plugin-aurora
```

  </CodeGroupItem>

  <CodeGroupItem title="NPM">

```shell:no-line-numbers
npm install hexo-theme-aurora hexo-plugin-aurora --save
```

  </CodeGroupItem>
</CodeGroup>

---

### Step 2 - Generate theme config

> **Config file `_config.yml` now need to be added in the root folder of your Hexo blog. You simply create a `_config.aurora.yml` to change the theme.**

To get a default theme template, for Linux (MacOS/Linux OS) users simply run the following command

For Windows users you can copy the template below into `_config.aurora.yml`.

Linux copy template command

```shell:no-line-numbers
cp -rf ./node_modules/hexo-theme-aurora/_config.yml ./_config.aurora.yml
```

Or copy this template from the link to the `_config.aurora.yml` file in project root.

https://github.com/auroral-ui/hexo-theme-aurora/blob/main/_config.yml

---

### Step 3 - Setting `theme`

Next update the `theme` config in `_config.yml` inside project root to `aurora`

1. Open the `_config.yml` in your hexo root direction.
2. Change `theme` to `aurora`

```yml:no-line-numbers{4}
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: aurora
```

---

### Step 4 - Setting `permalink`

> **Due to the use of Vue-router, the default Hexo generated pages and posts' permalink will cause the Vue router fail to find the route, therefore you need to change the Hexo default permalink configuration.**

1. Open the `_config.yml` in your hexo root direction.
2. Change `permalink` to `/post/:title.html`

```yaml:no-line-numbers{4}
# URL
## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
url: https://tridiamond.tech
permalink: /post/:title.html
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
  trailing_html: true # Set to false to remove trailing '.html' from permalinks
```

---

### Step 5 - Setting up code highlight

> **Last but not least, the theme use `Prismjs` for code highlighting, but Hexo default uses `highlightjs`, therefore you will need to change the Hexo config to use Prismjs instead:**

:::tip
All you have to do is change highlight's enable to `false` and change prismjs's enable to `true`
:::

```yaml:no-line-numbers{2,9-10}
highlight:
  enable: false
  line_number: true
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false
prismjs:
  enable: true
  preprocess: false
  line_number: true
  tab_replace: ''
```

---

### Step 6 - Creating the `about` page

The theme enables `about` page by default, therefore we should create it before using the theme.

To create a default about page, use the following `Hexo command`:

```shell:no-line-numbers
hexo new page about
```

After that, you will see a new folder had been created:

```shell:no-line-numbers
.
└── source
    └── about
        └── index.md
```

You can feel free to edit the markdown file inside the `about/` folder, the content will be displayed in your about page.

---

### Step 7 - Run local server

> **To run the local server and check out your blog, simply run the following command.**

```shell:no-line-numbers
hexo clean & hexo g & hexo server
```

:::tip
Any configuration changes will require you to regenerate all the Hexo static files!
:::

After all the files finish generating, you will be able to visit your blog on [https://localhost:4000](https://localhost:4000).

---

## What is next?

There are two places you should check out next:

1. Setting up your [Page](/guide/page.html)
2. Advance [configurations](/guide/configuration.html) document
