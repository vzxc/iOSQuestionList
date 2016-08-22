#3D Touch剖析（一）

作者：[喜洋洋与光头强](https://github.com/wjl626nice)

最近，终于闲下来了，作为账号开篇，给大家推送点干货！

21世纪，信息和科技爆炸的时代。Apple在上代设备（iPhone6s/6s Plus）上率先采用的3D Touch的技术，这一次，iPhone（以下的iPhone都默认为支持3D Touch）能够感应你对屏幕的按压力度，当你使用3D Touch的时候，iPhone将有轻微的触感，让你不仅仅能够看到按下屏幕的效果，还能感觉得到使我们日常操作手机的方式，为新一代iPhone的用户体验开拓出全新的纬度。

3D Touch到底给我们带来了哪些实际的操作的方式的颠覆？

首先，屏幕快捷方式。

以前，在屏幕的主界面上，app图标支持轻点（打开app），长按手势（编辑app），现在3D Touch给我们带来了app的全新操作方式-快捷方式。

如下图（图1-1）：

![Mou icon](https://mmbiz.qlogo.cn/mmbiz/g9QIzpmWFALZ6oibzrSXYD6Rlw4miaAKn9Y72maCic7CAWicUtDYHdBnJhbhPvMwCevrhVrVsjibddOc5uPJo1m4pGA/0?wx_fmt=png)

关于屏幕快捷方式特点

1. 当用户按压app图标的力度稍微大于轻点或长按的力度的时候，显示快捷方式。
2. 显示的信息包含有一个短标题、一个图标、和可选的子标题。
3. 不支持其他自定义的内容。
4. 当app更新后能显示更新信息。

当我们使用屏幕快捷方式的时候，需要注意一下几点：

1. 使用一个引人注目地、高效地、屏幕快捷方式。例如：Maps让用户在没有打开的情况下搜索当前位置附近，或者获取回家的方向。在主屏幕的每个应用程序需要至少一个有用的任务；你总共能提供四个快捷方式。
2. 避免使用与用户预期不同地方式来更改屏幕快捷方式。
3. 不要使用屏幕快捷方式作为通知用户的一种方式。
4. 为每一个屏幕快捷方式提供一个简洁的标题（和一个可选的子标题）和模板图标。
5. 不要使用表情来作为屏幕快捷方式的图标。
6. 系统会自动决定快捷方式的图标显示在列表的左边或者右边，这取决于当前app的图标在用户屏幕上的位置。

其次，Peek和Pop。

Peek让用户在不离开当前上下文的前提下，预览一个item并且执行相关的操作。

如下图：

Quick actions in a Safari peek（图2-1）

![p1](https://mmbiz.qlogo.cn/mmbiz/g9QIzpmWFALZ6oibzrSXYD6Rlw4miaAKn9wWnpxxA5uiaL4x1ztSzPon2KNueYD5ZhR9ia4qDcyQ2n2SbGeTQ8eYpw/0?wx_fmt=png)

A peek preview in Safari（图2-2）

![p2](https://mmbiz.qlogo.cn/mmbiz/g9QIzpmWFALZ6oibzrSXYD6Rlw4miaAKn9xyooXianXJNR2psNdtVjZ2NpAj8AsAI2SjVZ4myIyeib9xnqw8gH7ibgg/0?wx_fmt=png)

Peek和Pop功能特点

1. 当用户按压一个支持peek的item的时候，（如图2-1所示），显示item的预览视图，当用户手指离开的时候，预览视图消失。
2. 当用户按压的力度再大一点的时候，我们叫做Pop。打开item的详情界面。
3. 当用户在预览视图界面上向上扫动能够提供item详情界面有关的快捷方式（如图2-2所示）。

注意：一直贯穿你的应用程序采用peek 和 pop 是必要的。假如你在一些地方采用了，而在另外一些地方没有采用，用户可能会想在你的app中或者是他的设备上出现了问题呢！

使用Peek和Pop的时候，需要注意以下几点：

1. 用peek为一个item提供一个生动地、内容丰富地预览视图。例如：在用户决定在Safari中打开或者分享一个网页之前，能够用peek view预览网页的内容。
2. 为每一个peek提供一个pop。尽管peek需要给用户提供他们需要的大部分的信息，假如用户决定切换方式查看内容的时候，你需要一直让用户利用pop过渡到详情界面，户点击item查看的详情pop提供的是同一个view。
3. 在同一个item上不要同时支持peek和编辑菜单。
4. 如果合适，应该为预览视图提供peek快捷方式。
5. 不要使用peek作为item特殊操作的唯一途径。因为，目前市面上不是所有的设备都支持3D Touch，另外，用户可能在设置中关闭3D Touch功能。

最后，力度属性。

我们可以监测用户在屏幕上的按压力度，我们在iPad上素描的时候，可以根据按压的力度，决定线条的粗细程度。

总结：敞开胸怀，拥抱最新科技。相信3D Touch会很快应用在我们常用的app上。关于3D Touch的技术使用方法，我会在后面持续更新。欢迎关注！