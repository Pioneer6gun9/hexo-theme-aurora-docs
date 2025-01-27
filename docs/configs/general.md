# General

## Config File

There are two different configuration files, one is for **Hexo itself** and one for **the theme**.

```shell:no-line-numbers
. # Hexo project root.
├─ _config.yml # Hexo config file.
└─ _config.aurora.yml # Theme config file.
```

:::warning
Most feature of the theme is configured using the theme config file, except for those that require Hexo plugin's support.
:::

## Site Configs

The main settings of the blog is configured with the `site` config, it can be used to configure the **main information and settings** of your blog.

The `site` config has the following options:

|     Options      | Accepted Types | Usages                                                                                                                                    |
| :--------------: | :------------: | ----------------------------------------------------------------------------------------------------------------------------------------- |
|    `subtitle`    |     String     | Blog title, will be displayed after the current page title.                                                                               |
|     `author`     |     String     | Author of the blog, will be displayed in the **top header logo area**, also in the **profile widget**.                                    |
|      `nick`      |     String     | Sub header for the author, will be displayed below the author name in the logo area.                                                      |
|  `description`   |     String     | Used in the profile section, a few sentences to describe what you do or who you are. (Support HTML tags)                                  |
|    `language`    |     en, cn     | Setting the default locale of your blog.                                                                                                  |
| `multi_language` |  true, false   | Enabling the blog to have multi-language switching ability.                                                                               |
|      `logo`      |     String     | Link to your logo image.                                                                                                                  |
|     `avatar`     |     String     | Link to your avatar image.                                                                                                                |
|     `beian`      |     Object     | China website BeiAn information. (Since version 1.1.0, this had changed to have 2 properties.)                                            |
|  `started_date`  |     String     | The date this website/blog had started running. (Used for displaying how long the site had been running in the footer) Format: YYYY-MM-DD |

:::tip
If you did not set an `avatar` url, the logo's url will be used instead.
:::

---

### Beian Options

| Options  | Accepted Types | Usages        |
| :------: | :------------: | ------------- |
| `number` |     String     | Beian number. |
|  `link`  |     String     | Beian link.   |

---

### Police Beian Options

| Options  | Accepted Types | Usages        |
| :------: | :------------: | ------------- |
| `number` |     String     | Beian number. |
|  `link`  |     String     | Beian link.   |

---

## Config Example

```yaml:no-line-numbers
# Site Config
site:
  subtitle: TriDiamond's Blog
  author: TriDiamond
  nick: Frontend
  description: Seeking to deliver efficient and high quality programs. <br/> Senior Frontend Engineer
  language: en
  multi_language: true
  logo: https://image-website.com/path-to-image.jpg
  avatar: https://image-website.com/path-to-image.jpg
  beian: # Can leave number and link blank if you don't need this.
    number: "123123123123"
    link: 'https://link-to-beian.com'
  police_beian:
    number: "123123123123"
    link: 'https://link-to-police-beian.com'
  started_date: 2023-08-08
```
