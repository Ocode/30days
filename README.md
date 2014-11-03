30 天学习 30 种新技术系列
=========================

Learning 30 Technologies in 30 Days: A Developer Challeng

我呢，比较孤陋寡闻，最近几天才看到这篇系列(2014-10-29，这是巧合吗，刚好晚了一年阿，刚开始进度都比原作慢阿，惭愧阿)

发现这个系列真是不错，于是决定学习，刚一开始就碰壁呢，明明非常简单的一步步下来，但我系统中就是失效了（我在Ubuntu里的，问题解决后好多了），而进展第二天的学习进度时，又有问题呢，可能这个系列已经同步跟进API，也没有持续更新了，既然我要学习，就要解决这些问题，我想也做下记录吧，便于以后参考及注意！

突然想到原作者这个挑战真是不错，但如果再有下文就更好了阿，于是我想也许我可以继续挑战下，当然这是后话，也许没办法做到每天一种新技术，但是我尽力做到每天都有收获！也应了我的那博客之名《日有所获》，加油哦！

为方便学习，下面先把原文摘过来，方便大家对比参考，如有更正，将同在下面指出：


====================  华丽的分割线  ========================


#### 编者注：我们发现了比较有趣的系列文章《30 天学习 30 种新技术》，准备翻译，一天一篇更新，年终礼包。以下是译文，英文标题表示还未翻译，附原文链接；中文标题表示已翻译，附译文链接。

#### 更新：全系列已经全部翻译完成。

    让你 30 天学习 30 种新技术，你会觉得这是挑战吗？

![a-developer-challenge](img/a-developer-challenge.jpg "Learning 30 Technologies in 30 Days: A Developer Challenge")

我已经接受了挑战，我会在一个月的时间内每天学习一门新技术，挑战开始于 2013 年 10 月 29 日。下面就是我将要学习的新技术的列表，我会把每天学到的内容写出来。在我每天正常的工作之后，我会花几个小时学习一门新技术，再用一小时将今天学到的写在博客上。这项活动的目的是熟悉许多在开发者社区所使用的新技术。

我会把重点放在 JavaScript 及其相关技术的学习上，当然也会去了解一下像 Java 这类我比较感兴趣的其他技术。我也可能会在一门技术上花费好几天的时间，但我每次会选择和这门技术相关的不同的主题来讲。只要是有意义的，我将尽量展示它如何与 OpenShift 工作，我希望这是一次充满乐趣并能学到很多东西的旅程。（你可以在 twitter 上<a rel="nofollow" href="https://twitter.com/shekhargulati">follow 我</a>）

#### 下面是学习列表：

- 2013.10.29 - [Day 1: Bower——管理你的客户端依赖关系](http://segmentfault.com/a/1190000000349555)
- 2013.10.30 - [Day 2: AngularJS —— 对 AngularJS 的初步认识](http://segmentfault.com/a/1190000000350125)
- 2013.10.31 - [Day 3: Flask —— 使用 Python 和 OpenShift 进行即时 Web 开发](http://segmentfault.com/a/1190000000351512)
- 2013.11.01 - [Day 4: PredictionIO —— 如何创建一个博客推荐器](http://segmentfault.com/a/1190000000352163)
- 2013.11.02 - [Day 5: GruntJS —— 重复乏味的工作总会有人做（反正我不做）](http://segmentfault.com/a/1190000000353114)
- 2013.11.03 - [Day 6: 在 Java 虚拟机上使用 Grails 进行快速 Web 开发](http://segmentfault.com/a/1190000000353272)
- 2013.11.04 - [Day 7: GruntJS 在线重载 提升生产率至新境界](http://segmentfault.com/a/1190000000354555)
- 2013.11.05 - [Day 8: Harp.JS —— 现代静态 Web 服务器](http://segmentfault.com/a/1190000000355181)
- 2013.11.06 - [Day 9: TextBlob —— 对文本进行情感分析](http://segmentfault.com/a/1190000000356029)
- 2013.11.07 - [Day 10: PhoneGap —— 开发手机应用如此简单](http://segmentfault.com/a/1190000000357272)
- 2013.11.08 - [Day 11: AeroGear 推送服务器：使应用的通知推送变得简单](http://segmentfault.com/a/1190000000358740)
- 2013.11.09 - [Day 12: OpenCV —— Java 开发者的人脸检测](http://segmentfault.com/a/1190000000358809)
- 2013.11.10 - [Day 13: Dropwizard —— 非常棒的 Java REST 服务器栈](http://segmentfault.com/a/1190000000359827)
- 2013.11.11 - [Day 14：使用斯坦福 NER 软件包实现你自己的命名实体识别器（Named Entity Recognition，NER）](http://segmentfault.com/a/1190000000360213)
- 2013.11.12 - [Day 15：Meteor —— 从零开始创建一个 Web 应用](http://segmentfault.com/a/1190000000361440)
- 2013.11.13 - [Day 16: Goose Extractor —— 好用的文章提取工具](http://segmentfault.com/a/1190000000362182)
- 2013.11.14 - [Day 17: 使用 JBoss Forge 和 OpenShift 构建部署 JAVA EE 6 应用](http://segmentfault.com/a/1190000000363485)
- 2013.11.15 - [Day 18: BoilerPipe —— Java开发者的文章提取工具](http://segmentfault.com/a/1190000000363797)
- 2013.11.16 - [Day 19: EmberJS 入门指南](http://segmentfault.com/a/1190000000365519)
- 2013.11.17 - [Day 20: 斯坦福CoreNLP —— 用 Java 给 Twitter 情感分析](http://segmentfault.com/a/1190000000365547)
- 2013.11.18 - [Day 21：Docker 入门教程](http://segmentfault.com/a/1190000000366923)
- 2013.11.19 - [Day 22： 使用 Spring、MongoDB 和 AngularJS 开发单页面应用](http://segmentfault.com/a/1190000000367441)
- 2013.11.20 - [Day 23： 使用 TimelineJS 构建精美的时间轴](http://segmentfault.com/a/1190000000368066)
- 2013.11.21 - [Day 24: 使用 Yeoman 自动构建 Ember 项目](http://segmentfault.com/a/1190000000368881)
- 2013.11.22 - [Day 25: Tornado —— 联合 Tornado、MongoDB 和 AngularJS 进行应用开发](http://segmentfault.com/a/1190000000368729)
- 2013.11.23 - [Day 26: TogetherJS —— 让我们一起来编程！](http://segmentfault.com/a/1190000000370631)
- 2013.11.24 - [Day 27: Restify —— 在Node.js中构建正确的REST Web服务](http://segmentfault.com/a/1190000000369308)
- 2013.11.25 - [Day 28: OpenShift 的 Eclipse 集成](http://segmentfault.com/a/1190000000372498)
- 2013.11.26 - [Day 29: 编写你的第一个 Google Chrome 扩展程序](http://segmentfault.com/a/1190000000371543)
- 2013.11.27 - [Day 30: Play Framework —— Java 开发者的梦想框架](http://segmentfault.com/a/1190000000374033)


原文 [Learning 30 Technologies in 30 Days: A Developer Challenge](https://www.openshift.com/blogs/learning-30-technologies-in-30-days-a-developer-challenge)

翻译 [SegmentFault](http://segmentfault.com/a/119000000034938)


