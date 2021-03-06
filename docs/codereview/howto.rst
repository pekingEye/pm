如何进行code review？
=====================

code reivew是保障代码质量的实用方法之一，这里简单分享下个人code review的经验。建议只当案例来看，因为不同项目、不同团队所做的事情、所具备的技术背景也是不同的，当然也会有些通用的点。

现实情况
--------

先问下，你所在的公司有code review的习惯不？你所在的团队呢？你个人呢？如果没有的话，为啥会忽略这个环节呢？

来说下现实情况，大多数公司做的项目，如果按项目规模来看，都是很小的项目，即使是很大的项目，正确的做法也必然会拆分成多个小项目，由多个团队同时合作完成。在这个前提下，实际每天每个程序员提交的代码量是很少的，对这么少的代码变更进行code review其实是花不了个人多少时间的。

我觉得完全每天可以抽出半小时，乃至一小时的时间来对别人的代码进行review，比如：

* 或每天上班正式开始自己的工作前，边吃早点边code review别人昨天的几次提交。
* 或中午大桌聚餐在大液晶屏，边吃边评论互相的代码
* 或每天下班前花半个小时review下别人代码

只是随便举几个场景的例子，code review形式不限、时间、地点更无所谓。

不同的团队，不同的项目，在不同的时期，可能对代码发布的要求不同：

* 有的团队，对代码质量控制很严格，会规定凡是提交到主干的代码都必须经过review，严格保持主干的代码历史提交都是足够干净的；
* 但现实中也有很多团队，根据实际情况采用事后review，review后随时修正，不过这样看起来代码历史看起来不那么干净，但最后结果总还是不错的。

不管如何，我觉得做项目本身都没有十足的铁则，实用就好。

code review的目的
-----------------

团队中为什么要有code review的文化呢？或者说，code review有哪些好处吗？

从项目角度，很直接，可以提高代码质量。从人性弱点上来看，人类总是乐于去发现别人不好的地方的，所以多一双眼睛，更容易发现代码中的坏味道；另一方面，大家内心深处都是乐于追求真、善、美，所以总是希望写出来的代码更加优美。间接上，代码质量提高，对于一个项目的成功，以及一个软件的生命周期的延长，是个挺必要的因素，至少微观上是这样。

从个人角度，可以大致分两种。对于初学者学习，从看有经验人的代码过程中，可以学到好的代码实践；对于有经验的人自省，自然能发现各种不好的，时刻提醒让自己避免这种不好的代码，顺便可以帮助别人更好更快地提高，毕竟大家都是从初学者过来的。

从团队角度，逐渐拉近团队成员间的水平。尽管团队中成员各有所长，但在代码层面会有共同标杆，共同进步，让团队整体实力得到提高。

code review的形式
-----------------

code review的形式各种各样，这里按人数规模来分类。

1自审
~~~~~

这个其实是大家都在做的方式，但可能不一定每个人都能做得好，或者说人类总是很难自觉做到从自己身上发现问题，经过一定训练后逐渐会学会限制这种本能。一种方式可以有所帮助，就是找个木偶讲解代码，比如：放在桌上的瓦力小机器人或盆栽之类的东西。讲出你写的代码的变化，也许就会发现一些问题。

当然，一般都会借助一些工具来帮忙检查代码，比如：各种语言的lint工具或者很多IDE本身的功能，在代码风格这些偏静态层面的东西，可以辅助发现一些问题。

另外，随着程序员编程经验的增长，逐渐会注意到代码的各种坏味道，这也是给别人做code review的基础。

这种形式的code review，发现了问题基本上就是立马纠正了。或者说，自己已经处理了一大半的代码坏味道了，剩下可能真的自己都很难发现了，毕竟不是每个人的自省能力都是很高的，所以才有了后面的几种形式。

p2p互相
~~~~~~~

这种形式其实也很常见，特别是两个小伙伴一起协作编程的时候，比如：所谓的结对编程。当然，也可以不是结对编程，比如：两个人挨着坐，一个人完成一块逻辑复杂或稍有难度的代码后，需要别人来把把关，这个时候就可以叫上旁别的人帮忙过下代码或自己给他讲解下代码。

如果是结对编程，个人认为还是需要两人水平相当，一个人在一个显示器前写代码，另一个人在另一个复制的显示器前观察写的代码，有问题随时沟通，也许两人各有所长，一人完成某块他擅长的部分后，两人交换角色。这个时候，其实是个互相审核的过程。

当然，也有不在少数的人不习惯所谓结对编程，那么就各自干活，谁觉得需要另一个人帮忙，就进行code review。这种形式，个人觉得就不必要求两人水平相当，也可以一个老手+新手的组合。

另外，个人建议这种形式的code review，最好两人负责的任务是比较相似或有交集，效果会更好些，不然一个人不理解另一个人的业务逻辑，效果上还是会打些折扣的。

这种形式的code review，也是发现了问题基本上就是立马纠正了。如果这个时候提交代码，至少2个人看过了，或者说有2个人对这块代码负责了，也能从一定程度上对这块代码所具备的知识有了一份复制，软件这种东西的背后知识看不见摸不着，知识的复制备份尤其重要。

2-3单向
~~~~~~~

这种形式随着各种code review的工具出现，越来越方便，自然也就越来越流行了。这里的“2-3”意思并不是只有2个人或3个人，根据需要也可以再增加人数，特别是有很多code review工具辅助的时候。

这里特别强调是单向，说白了就是你提交了代码，别人来评论，赞一下或踩一下，当然写代码的人也不要把这些评论太过心，过脑即可，意思是说别人的评论都是善意的，别人好的建议或意见可以采纳，如果要拒绝可以向对方说明理由，就是觉得不爽时候别太放在心上。如果不习惯用各种code review辅助工具，可能就是比如：有2个人站在你后面，你指着显示器上的代码给他俩各种讲解，他们有疑问随时提问，你负责说明，也就是一问一答。如果有code review工具辅助，那就更方便了，大家直接看代码，然后在线对代码进行评论，比如：如果有2+以上人允许通过，那就可以提交，如果有人反对或有改进建议，就直接评论，各自的邮箱也能收到需要code review的任务和结果，那块代码的作者也可以根据评论来改进自己的代码。

当然，这个时候个人建议那2个人中，有至少一人是个老手，最好是那种什么扫地阿姨，背后一站，扫一眼就看出你这有个溢出那种。当然这是玩笑了，意思是得有个有经验的程序员把关。

另外，至于是否对这块代码有了解或熟悉，就可以不用像上一种“p2p互相”那种形式要求的那样，大家最好都要对这块代码熟悉了。

这种形式的code review，一般是由写代码的人负责记录问题，当然有code review工具辅助，那就工具自动给你记录了，省去很多麻烦。这种形式也是最省事的，特别是有了工具辅助，也就没有时间、地点的限制了。

>3展示
~~~~~~

这种形式有点会议形式，更接近“代码审查”了，而不是“代码评审”，一堆人圆桌+大屏。如果有场景，的确要用到这种形式的code review那就要慎用了，大家都知道一旦变成开会形式了，那就必然会有会议的各种缺点出现，所以要注意。

* 首先，得有个主持人，无特定人员要求，也可以是写代码的那个人，没有关系，关键这个主持人能控场，别让偏题了，毕竟人多口杂。
* 其次，必须举手发言，不然容易变成聊天。
* 最后，避免争论或者叫吵架吧，可以讨论或叫沟通吧，互相不要对着人说话，而是对着某个物件来说话，比如：前面提到的那个瓦力机器人和盆栽，这样能一定程度上避免出现争论或吵架的情况。

当然，一旦开会形式了，针对某个人写的代码，容易变成批评、批斗，所以还得要注意：

* 不要去关注谁写的代码
* 对代码不对人
* 重点在业务逻辑或代码设计实现
* 弱化代码风格的评价

  + 除非展示目的是为了大家了解代码风格
  + 除非代码风格让人没法进行代码的审查

另外，如果没有强烈的特别的需要，其实还是不要这种形式的code review了，主持人不好或大家意识上不到位，容易浪费时间，效果不一定好。

这种形式的code review，可以指定一个记录人，当然就和主持人不是一个人了，不然主持人即当爹又当妈，功能不要太全哦！当然最好可以是写代码的那个人。

其它
~~~~

这里说些其它形式的code review。可以引入某方面的专业人士，比如：安全专家，对代码进行安全层面的审计，虽然程序员必须具备安全意识，但安全层面的思路有时候还是会有所差异的，毕竟每个人的安全意识水平也参差不齐；再比如，需要对数据库或操作系统等的特别操作，可以让这方面的专家帮忙把关，当然如果团队中有这些类型角色的成员，就再好不过了。

最后，提几个建议，可能上面说过：

* 针对代码，不针对人。但另一方面代码毕竟人写的，所以需要注意评论的方式。
* 提出评论的人，可以采用发问的形式评论，比如：是不是XXXX这样改，这块代码执行起来就会更加OOOO了？类似这样的语气
* 被评论代码的人，别有抵触心理，要有空杯心态，就是上面说的过脑但别过心了。
* 程序员这个群体，并不是所有人都是天才级别的，所以当你看到别人写的烂代码时候，也得知道自己当初也可能经历过那个阶段。

code review的重点
-----------------

本来想说下，哪些地方需要重点code review，但发现场景不同，项目不同，采用的技术不同，大家的关注点都不一样，如果说成通用的，反而没有重点了。比如：大段代码、大函数、大类、长SQL、复杂存储过程、使用频率高的功能、代码嵌套太深、核心算法实现、核心接口实现、函数参数过多、用户输入校验是否有安全隐患、异常处理、日志记录、业务是否需要事物等等太多了。

另外，不同编程语言、编程框架还有不同规范性质的编程建议，实在不好说重点。

如果要看重点，估计还是自己去翻一遍《代码大全》比较实际。

code review的工具
-----------------

code review有很多工具，最原始的莫过于人肉了，这里简单列举下几个工具，看各自实际情况使用了。一般对这种类型工具或软件的要求可能有：

* 可以评论，跟代码关联程度高，然后最好能跟网易评论似的各种嵌套。
* 可以邮件提醒。
* 可以很好支持Git或SVN等版本控制工具。
* 可以很好支持Jenkins等CI工具。
* 可以支持命令行，方便写脚本集成其它工具。

列举下我知道的工具：

* Trac插件：Code Comments。如果用的Trac管理项目，可以用下，但没有上面说的具备的要求那么全。
* Review Board。一个Python写的Web类型工具。
* Facebook Phabricator。小有名气，Facebook出品，应该人家内部自己做项目都用的这个，功能有点太全了，可能如果单做code review，会有点晕。
* Gerrit。一个Java写的Web工具，可以和Jenkins很好结合，也算好用。
* Code：豆瓣出品，没用过，但据说不错。

另外，用了工具后，别忘了还有最实用的面对面交流这个人肉工具，也许用惯了冷冰冰的工具外，小伙伴互相看完代码后，温暖的会心一笑还是不错的。

最后
----

* code review多在平时的零散时间。
* 贵在坚持、积累，让code review成为呼吸一样理所当然的事情吧。
* 对代码质量有更多提高效果的其实是“code review的形式”说的平时的前3种情况。
* 某种角度说，代码是产品、项目、软件的基石，还是需要关注下的。

有关code review的趣评（来自网上，出处不详）：

* 如果代码变更在几十行内，能写出一堆评论
* 如果代码变更成百上千了，基本都一个评论，“你的代码不错~”

其实想表达的意思是，递交的代码让别人review不要太爆炸了，别人会很有压力的。

后续，有关code review的主题，会具体介绍下几个常用的code review工具的安装和使用。
