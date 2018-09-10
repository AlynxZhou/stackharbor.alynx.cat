---
title: 无尽的咏叹回荡于伽蓝之世界中 —— 有关 ARIA
layout: post
comment: true
date: 2018-05-05 23:49:53
categories:
  - 计算机
  - 网络
  - 网站
  - Hexo
  - ARIA
tags:
  - Hexo
  - ARIA
---
大约从我写好 ARIA （指把我自己的网站换成它做主题）到现在为止已经有一个月了，这一个月里它有了 [20 个 Star](https://github.com/AlynxZhou/hexo-theme-aria/stargazers)、[4 个 Issue](https://github.com/AlynxZhou/hexo-theme-aria/issues?q=is%3Aissue+is%3Aclosed) 和 [128 个 Commit](https://github.com/AlynxZhou/hexo-theme-aria/commits/master)（都是我自己，残念啊）。大概算是我现在最得意的项目，当然不排除以后也是。

虽然这么说有点敷衍，但是我是和一些无聊的人进行了一点无谓的争执 —— 我讨厌辩论，所以尽可能把这种冲动压制在一点 —— 所以我现在来写这篇文章，聊聊那些代码里面没有告诉你的事情。写点经过脑子的思考总是有用处的，不仅是对自己而言。

<!--more-->

我已经不太记得当初自己选择 Hexo 的理由了，大概是因为 2016 年的时候比较热门的静态博客生成器就是 Jekyll、Octopress 和 Hexo 吧。我不太注意 Pelican 是什么时候出现的，至于 Hugo，没记错的话 Hexo 冲上 [staticgen](https://www.staticgen.com/) 前三的时候，Go 语言还是个尝鲜的状态，然后才有了 Hugo。那时候大概还没有 React.js，所以也就没有 Gatesby。

Hexo 当初打出的招牌就是它比 Jekyll 和 Octopress 快，当然现在 Octopress 已经式微了，Jekyll 作为 GitHub 钦定的生成器还是好好的。选择了 Hexo 才发现相比其他生成器，Tommy351 是台湾人这一点让它有更好的中文文档支持 —— 对一个新手来说还是很重要的。习惯了之后就没有必要换另一个的代价，何况它们并没有太大的吸引力。我对 Go 并不是很感兴趣，Hugo 的“第一快”和 Hexo 的“飞快”比起来也并不是一个充足的理由。至于 Gatesby —— 我还要学 React，然后 AJAX 获取数据更新页面然后突然换掉地址栏地址这种行为单纯的觉得不舒服。

所以 Hexo 看起来完全够用，还要算上各种奇怪的插件，不同的模板和预处理器，另外我是因为 Hexo 才对 Node.js 产生好感的。

那为什么要自己写一个主题呢，一部分的原因是已经用腻了 NexT，老实说我不是很喜欢这个名字，很想问问作者是不是在看了乔布斯传里面的 NeXT 才想了这么一个名字。它让我想起一个观点叫做“第一个把女人比作花的是天才，第二个把女人比作花的是庸材，第三个把女人比作花的是蠢材”，感谢语文老师。

不过说到底起什么名字是人家的自由，也不能不说它是个不错的主题。然而人是一种不做点什么就不好感知自己存在的生物，因此做这个项目除了因为 NexT 几个 Scheme 和遗留代码混在一起让我觉得难以掌握，以及 Swig 已经被废弃了但这个主题却很难迁移的强迫症之外，还有“我做是为了证明我能做”的念头，最后就是深层次的“让痛苦来证明我还活着”（黑执事 1 的结尾？）。

虽说如此，我一直没有足够的动力来写，最后只能是碌碌无为地做一些其他的事情。

直到听说 Kalafina 要解散的时候，我觉得自己应该给她们做点什么，虽然自己好像什么也做不到，但是给自己的主题起个名字总是可以的吧。那张红色封面的 ARIA 是我至今听过的最出色的 LIVE，甚至超出录音室的版本。

在写 ARIA 的时候我给自己定了几个目标，比如说我实在是受不了许多主题高喊着一个比一个简洁然后却很丑的状况（这个观点也是在别人那里看到的，一群人自以为是简洁，实际是简陋），所以就算做的复杂一点（并没有这个能力）也要让它看起来优雅（emm 如果大家觉得现在的样子符合这个标准的话）；再比如我也不想编辑一份超过 500 行的配置文件，在一大堆应该保持默认值的选项里找几个人人都想改的选项实在是太愚蠢了（“你为什么非要过那 1% 的生活？”）（前面只是玩梗），如果大家都这样设置，那就写死到代码里好了，如果人人都想改成另一种选项，那应该把那种设置成默认值；最后就是如果可能的话尽量不要用 `position: fixed;` 或者 `position: absolute;` 还有 `position: float;` 这种属性，即使用一些比较新的 CSS 属性（IE 10 以下的不配看我的网站！），因为它们对我来说太不直观又难以驾驭了。

然后就是选择模板和预处理器了，ejs 这种又挫又丑的东西我是不会去用的，然后看起来 Hexo 的 Nunjucks 插件还算能用（当然并不好用，都没人更新了还占着最好的名字，于是我只能自己写了一个，这是后话），唯一对 Nunjucks 不满的地方大概是它的关键字是 Python 风格（我讨厌这两种叫做 Python 的语言）。CSS 预处理器看起来在 Sass 和 Less 之间有个更好的选择叫做 Stylus（也是 Node 社区比较喜欢用的），既然这次是自己写样式了，纠结了好久我还是没有添加 Bootstrap。

参照的原型是 [hexo-theme-hueman](https://github.com/ppoffice/hexo-theme-hueman)，我很喜欢它的风格，但是看起来 Ppoffice 维护了好几个主题，但是哪个都不是很精细好用，当然随着我的设计进行 ARIA 和 Hueman 产生了不一样的设计，我比较喜欢现在的样子。

在艰难地摸掉了 Hexo、hexo-renderer-nunjucks（就是这个坑货不更新还占着好名字） 和 Stylus 的一些坑之后，开始正式的进入到编写阶段，果然对于我而言 CSS 才是最难驾驭的语言，不过还是顶着各种困难把它做成了我想要的样子（优秀的前端工程师想要什么样就做成什么样，我是做成什么样就算什么样），其中的经历不太想多说，比如 Hexo 的中文文档没有告诉我 page.posts 是个什么类型（不是 Array，ejs （就是嵌入的 JavaScript）可以迭代，但是 Nunjucks 却不行），英文文档又出现了 Array of `???`，请问 `???` 是什么？点击链接又跳转到了 Hexo 的一个叫做 Warehouse 的子项目，这又是什么？后来终于我在 Issue 列表里找到了答案，这是个数据库，为了能让 Nunjucks 和 Swig 迭代，作者又添加了个 `toArray()` 方法。再比如 hexo-renderer-nunjucks 的版本卡在 Nunjucks 2，我又自己写了个插件支持 Nunjucks 3。还有自己差不多完全重写了一个用来搜索的 js。好在最后是做出来了。

比起做加法，做减法看起来更难一点，首先由于翻转的 CSS 动画莫名的消耗了 chrome 的性能，让我把它改成了可选项。然后觉得按钮鼠标覆盖转两圈太花哨了，改成了阴影。然后踢掉了不必要的自定义不蒜子字符串的设置项。最后怎么看那个灰色的“阅读原文”按钮怎么觉得它和风格不搭，同时又和文章标题功能重复，终于下决心把它删掉了。大约是一边狂奔一边丢掉所有东西的人生的剪短缩影。

这就是你现在看到的它的样子，没有什么文章头图这种设计，纯粹是因为这个写起来太不直观，文章的核心始终是在文字内容上，为什么非要花时间去找一张图片搭配给它做头图呢？比起这个，各种链接的变色的细节才是我想要的。说到底，还是为了在这个世界里留下一点自己独特（固执）的存在。

如果说还有什么要加进去的话，短期内是自定义字体的设计，现在的字体顺序是我最喜欢的字体排在最前面，但看起来似乎大家有不一样的喜好。

请务必记住我对这个世界无尽的咏叹，记住这个在深夜里写一点话的孤独的灵魂。

*AlynxZhou*

**A Coder & Dreamer**