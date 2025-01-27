# 插件

这个主题支持几个不同的插件。每个插件都将为主题提供高级特性。

> 在不久的将来会添加更多的插件!

## 多个作者

这个插件用来支持`多作者`，这个特性是为多个作者的博客或社区设计的。

这个概念是这样的，作为默认的作者，没有必要在每个帖子的 markdown 文件中反复配置作者。因此，在 [site configure](/zh/guide/configuration.html#site-configs) 中，有一个 author 属性用来设置默认的博客作者。一旦设置了这个值，你所有的文章都会继承默认的作者，除非在文章中重新定义。

为每篇文章设置不同的作者有两种方法：

> - 从版本 [`v1.2.x`](https://github.com/auroral-ui/hexo-theme-aurora/releases/tag/v1.2.0) 开始，`author` 支持更多的属性。
> - 版本 `v1.4.3` 多作者支持配置**自定义媒体链接**。

:::tip
多作者支持自定义媒体链接，在 `author` 的 `socials` 属性里面支持配置 `customs` 配置，自定义媒体链接配置请参考[媒体链接部分的文档](zh/guide/social.html#自定义社交链接)。
:::

**方法 1** - 在文章的 markdown 文件的**Front-Meta**中配置 author 属性。

```markdown:no-line-numbers
---
title: Article Title
date: 2020-08-15 18:49:36
tags:
  - Tag
categories:
  - Cate
cover: https://cover.png
author:
  name: TriDiamond
  link: https://tridiamond.tech
  avatar: https://avatar.png
  description: 'Think like an artist, code like an artisan.'
  socials:
    github: https://github.com/tridiamond
---
```

---

**方法 2** - 为网站预配置作者列表，然后在文章“author”属性中使用预配置的作者键。

- 首先你需要预先配置一个作者列表在主题配置文件，这是在 `_config.aurora.yml`。

```yaml:no-line-numbers
authors:
  author-1:
    name: TriDiamond
    link: https://tridiamond.tech
    avatar: https://avatar.png
    description: 'Think like an artist, code like an artisan.'
    socials:
      github: https://github.com/tridiamond
  author-2:
    name: Jerry
    avatar: https://Jerry.png
    link: https://github.com/TriDiamond
    description: 'I am Jerry, how are you?'
    socials:
      github: https://github.com/Jerry
```

- 然后你可以在文章的**Front-Meta**中使用 `author` 的 key 来设置作者。

```markdown:no-line-numbers
---
title: Article Title
date: 2020-08-15 18:49:36
tags:
  - Tag
categories:
  - Cate
cover: https://cover.png
author: author-1
---
```

:::tip
如果没有为篇文章设置`author`属性，博客的默认作者将被用作文章的作者。
:::

## 评论

这个主题目前支持两个不同的评论插件。您可以使用`enable`配置来打开以下一款评论插件。

:::tip
如果你同时打开了两个插件，**Gitalk**将会优先被使用。
:::

### Gitalk

配置属性：

|         属性          | 描述                                                                                                                                                                         |
| :-------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|       `enable`        | 使用**true**开启, 使用**false**关闭                                                                                                                                          |
|     `autoExpand`      | 如果设置为**true**, Github 评论将会自动展开。否者默认会收起。                                                                                                                |
|      `clientID`       | **clientID** 是你 GitHub 的 Oauth APP 中提供的。                                                                                                                             |
|    `clientSecret`     | **clientSecret** 是你 GitHub 的 Oauth APP 中提供的。                                                                                                                         |
|        `repo`         | 仓库名, 比如: https://github.com/auroral-ui/**hexo-theme-aurora-docs**, 名字就是 `hexo-theme-Aurora-docs`                                                                    |
|        `owner`        | 仓库拥有者的用户名. 比如: `auroral-ui`                                                                                                                                       |
|        `admin`        | 仓库管理员的用户名，这里可以填写多个管理员。(也用于标记那个评论是博主的)                                                                                                     |
|         `id`          | **确保唯一性和长度小于 50**，如果您使用`pathname`，请确保长度小于 50 个字符或使用`uid`代替，这个有更好的兼容性 (如果您之前使用其他主题，谁用 uid 将可能无法显示您之前的评论) |
|      `language`       | 使用 `en ` 设置为英文，使用 `cn` 设置为中文.                                                                                                                                 |
| `distractionFreeMode` | 与 Facebook 一样的专注模式，点击评论输入框时会让背景变暗。`true` 来开启 `false` 来关闭                                                                                       |
|    `recentComment`    | 是否开启最近评论功能。                                                                                                                                                       |
|        `proxy`        | GitHub 授权请求的反向代理                                                                                                                                                    |

**Template**

```yaml
# For local development only!
gitalk:
  enable: true
  autoExpand: true
  clientID: ''
  clientSecret: ''
  repo: '' ## dev-blo-comments
  owner: '' ## owner name
  admin: [''] ## ['admin_name']
  id: uid
  language: en
  distractionFreeMode: true
  recentComment: true
  proxy: ''
```

:::warning
如果你在使用 Gitalk 的时候，出现 403 或者 422 这种报错的话，请根据[这里的教程](https://mjava.top/archive/33f09b03-a5a7-4d66-93d3-7063905f9b81/)，自己搭建一个反向代理服务，然后把你建立好的方向代理地址配置给 `proxy` 即可。
:::

更多的使用指南请查看 [Gitalk's](https://github.com/gitalk/gitalk/blob/master/readme-cn.md) 插件的官网。

### Valine

配置属性：

|      属性       | 描述                                                             |
| :-------------: | :--------------------------------------------------------------- |
|    `enable`     | 使用**true**开启, 使用**false**关闭.                             |
|    `app_id`     | 从 LeanCloud 的应用中得到的 `app_id`.                            |
|    `app_key`    | 从 LeanCloud 的应用中得到的 `appKey`.                            |
|    `avatar`     | [Gravatar](https://valine.js.org/en/avatar.html) 头像展示方式。  |
|  `placeholder`  | 评论框占位提示符。                                               |
|    `visitor`    | 文章访问量统计。                                                 |
|     `lang`      | 如需自定义语言，请参考 [i18n](https://valine.js.org/i18n.html)。 |
|     `meta`      | 评论者相关属性。 `['nick','mail','link']`                        |
|     `admin`     | 用于标记那个评论是博主的                                         |
| `recentComment` | 是否开启最近评论功能。                                           |

**Template**

```yaml
# Valine comment plugin (recommended!)
# see https://valine.js.org/quickstart.html
valine:
  enable: false
  app_id:
  app_key:
  avatar: ''
  placeholder: Leave your thoughts behind~
  visitor: true
  lang: en
  avatarForce: false
  meta: ['nick', 'mail']
  requiredFields: ['nick', 'mail']
  admin: '' # admin username
  recentComment: true
```

更多的使用指南请查看 [Valine's](https://valine.js.org/) 插件的官网。

### Twikoo

配置属性：

|      属性       | 描述                                                            |
| :-------------: | :-------------------------------------------------------------- |
|    `enable`     | 使用**true**开启, 使用**false**关闭.                            |
|     `envId`     | 腾讯云环境填 envId；Vercel 环境填地址（https://xxx.vercel.app） |
| `recentComment` | 是否开启最近评论功能。                                          |

**Template**

```yaml
# Twikoo comment plugin
# see https://twikoo.js.org/quick-start.html
twikoo:
  enable: false
  recentComment: true
  envId: xxxxxxxxxxxxxxx # 腾讯云环境填 envId；Vercel 环境填地址（https://xxx.vercel.app）
  # region: ap-guangzhou # 环境地域，默认为 ap-shanghai，腾讯云环境填 ap-shanghai 或 ap-guangzhou；Vercel 环境不填
  lang: 'en' # 用于手动设定评论区语言，支持的语言列表 https://github.com/imaegoo/twikoo/blob/main/src/client/utils/i18n/index.js
```

更多的使用指南请查看 [Twikoo's](https://twikoo.js.org/) 插件的官网。

### Waline

配置属性：

|       属性       | 描述                                                                                                                                                 |
| :--------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------- |
|     `enable`     | 使用**true**开启, 使用**false**关闭.                                                                                                                 |
|    `reaction`    | 为文章增加表情互动功能，设置为 true 提供默认表情，也可以通过设置表情地址数组来自定义表情图片，最大支持 8 个表情。                                    |
|     `login`      | 登录模式状态，可选值: `'enable'`: 启用登录 (默认); `'disable'`: 禁用登录，用户只能填写信息评论 ; `'force'`: 强制登录，用户必须注册并登录才可发布评论 |
|      `meta`      | 评论者相关属性。可选值: `'nick'`, `'mail'`, 'link'                                                                                                   |
|  `requiredMeta`  | 设置必填项，默认匿名，可选值: `[]`, `['nick']`, `['nick', 'mail']`                                                                                   |
| `commentSorting` | 评论列表排序方式。可选值: `'latest'`, `'oldest'`, `'hottest'`                                                                                        |
| `imageUploader`  | 你可以设置为 `false` 以禁用图片上传功能。                                                                                                            |
|   `wordLimit`    | 评论字数限制。填入单个数字时为最大字数限制。设置为 `0` 时无限制。                                                                                    |
|    `pageSize`    | 评论列表分页，每页条数。                                                                                                                             |

**Template**

```yaml
# Waline comment plugin
# see https://waline.js.org/guide/get-started/
waline:
  enable: false
  recentComment: true
  reaction: false
  login: 'disable'
  meta: ['nick', 'mail']
  requiredMeta: ['nick', 'mail']
  commentSorting: 'latest'
  serverURL: '' # Server URL
```

更多的使用指南请查看 [Waline's](https://waline.js.org/) 插件的官网。

## 智能机器人 Dia (小钻)

![](https://img-blog.csdnimg.cn/20210415202611382.gif)

> `Dia` 是版本 1.4.0 加入的

当你的读者访问你的网站时，这个可爱的小家伙会和你在一起。

Dia 将对你的读者所采取的 `特定行为` 做出反应，并帮助你的读者在你的博客上浏览。

但这并不是黛娅唯一能做的事。Dia 还将为你的读者提供`每日引用`、`节日问候` 和 `随机信息`，给你的访问者带来意想不到的惊喜。

### 机器人配置

我们的 `Dia` 有很多配置。

Dia 已经安装了默认的对话系统，你可以简单地使用 `enable` 属性打开机器人，并使用 `locale` 属性更改语言。

一个简单的配置是这样的:

```yaml
# 开启 Aurora 机器人 Dia
aurora_bot:
  # ======================================================
  # 设置为 true，你可爱的机器人就会启动。
  # ======================================================
  enable: true
  # ======================================================
  # 该机器人支持两种语言
  # -- en: 英语
  # -- cn: 中文
  # ======================================================
  locale: en
  # ======================================================
  # 目前只支持使用 Dia，将来会支持 live2d。
  # ======================================================
  bot_type: dia
```

然而，如果你想完全改变谈话系统的内容，你也可以在你的 `_config.aurora.yml` 的配置文件中修改。

Dia 的配置可以如下这样配置:

```yaml
# 开启 Aurora 机器人 Dia
aurora_bot:
  # ======================================================
  # 设置为 true，你可爱的机器人就会启动。
  # ======================================================
  enable: true
  # ======================================================
  # 该机器人支持两种语言
  # -- en: 英语
  # -- cn: 中文
  # ======================================================
  locale: en
  # ======================================================
  # 目前只支持使用 Dia，将来会支持 live2d。
  # ======================================================
  bot_type: dia

  # 这个技巧是用来对用户交互做出反应的
  tips:
    # ======================================================
    # 这些是 Dia 每30秒会说的随机消息。
    # ======================================================
    messages:
      - 你好，我是 <span>Dia</span>，好高兴遇见你～
      - 好久不见，日子过得好快呢……
      - '<span>大坏蛋！</span>你都多久没理人家了呀，嘤嘤嘤～'
      - 嗨～快来逗我玩吧！
      - 拿小拳拳锤你胸口！
      - 学习使我们快乐，快乐使我们更想学习～
      - 你知道吗？你可以<span>点击我</span>返回页面顶部哦！～
      # 这是一个特殊的函数，它将触发 quotes API
      # 和 Dia 会说出每日引用的信息。
      - showQuote

    # ======================================================
    # 将在用户打开浏览器控制台时触发。
    # ======================================================
    console: 哈哈，你打开了控制台，是想要看看我的小秘密吗？

    # ======================================================
    # 当用户从你的博客上复制内容时触发。
    # ======================================================
    copy: 你都复制了些什么呀，转载要记得加上出处哦！

    # ======================================================
    # 这将在用户返回窗口时触发。
    # ======================================================
    visibility_change: 老朋友，你怎么才回来呀～

    # ======================================================
    # 欢迎留言，号码是一天中的时间。
    # -----------------------------------
    # eg: 24 = 00:00 也就是午夜
    # eg: 17-19 = 在下午 5 点到 7 点之间
    # -----------------------------------
    # 在一天的这段时间里，Dia 会向你的读者问好
    # 与相应的消息。
    # ======================================================
    welcome:
      '24': 你是夜猫子呀？这么晚还不睡觉，明天起的来嘛？
      '5_7': 早上好！一日之计在于晨，美好的一天就要开始了。
      '7_11': 上午好！工作顺利嘛，不要久坐，多起来走动走动哦！
      '11_13': 中午了，工作了一个上午，现在是午餐时间！
      '13_17': 午后很容易犯困呢，今天的运动目标完成了吗？
      '17_19': 傍晚了！窗外夕阳的景色很美丽呢，最美不过夕阳红～
      '19_21': 晚上好，今天过得怎么样？
      '21_23':
        - 已经这么晚了呀，早点休息吧，晚安～
        - 深夜时要爱护眼睛呀！

    # ======================================================
    # 当用户来自搜索引擎时使用。
    # ======================================================
    referrer:
      # 用户来自你自己的网站。
      self: 欢迎来到<span>「[PLACEHOLDER]」</span>
      # 用户来自百度搜索引擎。
      baidu: Hello！来自 百度搜索 的朋友<br>你是搜索 <span>「[PLACEHOLDER]」</span> 找到的我吗？
      # 用户来自360搜索引擎。
      so: Hello！来自 360搜索 的朋友<br>你是搜索 <span>「[PLACEHOLDER]」</span> 找到的我吗？
      # 用户来自谷歌搜索引擎。
      google: Hello！来自 谷歌搜索 的朋友<br>欢迎阅读<span>「[PLACEHOLDER]」</span>
      # 用户来自另一个网站。
      site: Hello！来自 <span>[PLACEHOLDER]</span> 的朋友
      # 任何其他来源。
      other: 感谢您阅读： <span>「[PLACEHOLDER]」</span>

    # ======================================================
    # 当你的'鼠标悬停'到特定的HTML标签，Dia将
    # 给用户留言帮助他们解决问题。
    # ------------------------------------------------------
    # selector: 标签选择器(你可以使用任何css选择器)
    # text: 这是Dia将要传达的信息。(如果你想要的
    #       Dia从一组信息中随机说出一个，设置它
    #       数组，否则只是纯文本)
    #  ======================================================
    mouseover:
      # 悬浮在 Dia 上
      - selector: '#Aurora-Dia'
        text:
          - 哇啊啊啊啊啊啊... <span>你想干嘛</span>? O.O
          - 请您轻一点，我是<span>很昂贵</span>的机器人哦! O.O
          - '<span>领导，我在呢!</span> 我有什么可以帮到你呢? O.O'
      # 悬浮在 Home 菜单
      - selector: "[data-menu='Home']"
        text:
          - 点击前往首页，想回到上一页可以使用浏览器的后退功能哦。
          - 点它就可以回到首页啦！
          - 回首页看看吧。
      # 悬浮在 About 菜单
      - selector: "[data-menu='About']"
        text:
          - 你想知道我家主人是谁吗？
          - 这里有一些关于我家主人的秘密哦，要不要看看呢？
          - 发现主人出没地点！
      # 悬浮在 Archives 菜单
      - selector: "[data-menu='Archives']"
        text:
          - 这里存储了主人的所有作品哦！
          - 想看看主人的图书馆吗？
      # 悬浮在 Tags 菜单
      - selector: "[data-menu='Tags']"
        text:
          - 点击就可以看文章的标签啦！
          - 使用标签可以更好的分类你的文章哦～
      # 悬浮在 language 菜单
      - selector: "[data-dia='language']"
        text: 主人的博客支持多种语言。
      # 悬浮在黑白切换按钮上
      - selector: "[data-dia='light-switch']"
        text: 您可以点击这里切换黑白模式哦！
      # 悬浮在作者简介上
      - selector: "[data-dia='author']"
        text:
          - 这是我主人的简介。
          - 点击其中任何一个链接都可以传送到我主人的其他世界。
      # 悬浮在作跳转评论按钮上
      - selector: "[data-dia='jump-to-comment']"
        text:
          - 你想看看评论吗?
          - 点击这里可以帮助你直接跳转到评论部分。

    # ======================================================
    # 当你的'鼠标点击'为特定的HTML标签，Dia将
    # 给用户留言帮助他们解决问题。
    # ------------------------------------------------------
    # 属性与' moveover '事件相同
    # ======================================================
    click:
      # 鼠标点击搜索按钮
      - selector: "[data-dia='search']"
        text:
          - 没有看到你想要的文章，那么就输入你想搜索的关键词吧～
          - 可以使用 ctrl/cmd + k 快捷键打开搜索哦～
      # 鼠标点击文章标题
      - selector: "[data-dia='article-link']"
        text:
          - 希望你会喜欢这篇文章：<span>「{text}」</span>.
          - 您的选择真的不错哦！好好享受这篇文章吧～
          - 希望您能从 <span>「{text}」</span>这篇文章中学到点东西。
      # 鼠标点击跳转评论输入框（Gitalk）
      - selector: '.gt-header-textarea'
        text:
          - 要吐槽些什么呢？
          - 一定要认真填写喵～
          - 有什么想说的吗？
          - 如果觉得文章不错的话，就给博主留个言吧～
      # 鼠标点击跳转评论输入框（Valine）
      - selector: '.veditor'
        text:
          - 要吐槽些什么呢？
          - 一定要认真填写喵～
          - 有什么想说的吗？
          - 如果觉得文章不错的话，就给博主留个言吧～

    # ======================================================
    # 在特定的日期，Dia会向你的读者问候。
    # ------------------------------------------------------
    # date: 特别活动的日期(格式:月/日或月/日-月/日)
    # text:
    # ---只使用一个简单的字符串。
    # -——消息的随机集合，使用数组配置格式。
    # ======================================================
    events:
      - date: 01/01
        text: '<span>元旦</span>了呢，新的一年又开始了，今年是{year}年～'
      - date: 02/14
        text: 又是一年<span>情人节</span>，{year}年找到对象了嘛～
      - date: 03/08
        text: 今天是<span>国际妇女节</span>！
      - date: 03/12
        text: 今天是<span>植树节</span>，要保护环境呀！
      - date: 04/01
        text: 悄悄告诉你一个秘密～<span>今天是愚人节，不要被骗了哦～</span>
      - date: 05/01
        text: 今天是<span>五一劳动节</span>，计划好假期去哪里了吗～
      - date: 06/01
        text: '<span>儿童节</span>了呢，快活的时光总是短暂，要是永远长不大该多好啊…'
      - date: '09/03'
        text: '<span>中国人民抗日战争胜利纪念日</span>，铭记历史、缅怀先烈、珍爱和平、开创未来。'
      - date: '09/10'
        text: '<span>教师节</span>，在学校要给老师问声好呀～'
      - date: 10/01
        text: '<span>国庆节</span>到了，为祖国母亲庆生！'
      - date: 11/05-11/12
        text: 今年的<span>双十一</span>是和谁一起过的呢～
      - date: 12/20-12/31
        text: 这几天是<span>圣诞节</span>，主人肯定又去剁手买买买了～
```
