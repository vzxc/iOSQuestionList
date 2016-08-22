#3D Touch剖析（二）
作者：[喜洋洋与光头强](https://github.com/wjl626nice)

前段时间我简单剖析了下3D Touch技术给我们带来了哪些实际的操作的方式的颠覆，那么怎么样使用这样技术呢？下面我们来举例说明。

回顾下3D Touch具体包含哪些方面:

1. 屏幕快捷方式，
2. Peek和Pop，
3. 力度属性。

首先，屏幕的快捷方式。

最好的快捷方式预期并且加快了用户的交互。iOS9 SDK提供了让你定义快捷方式的APIs。快捷方式分为静态和动态两种类型。

* 在你的app的Info.plist文件中添加一个键为 UIApplicationShortcutItems 的数组，然后在其中定义静态的快捷方式。

![shortcutitem](https://mmbiz.qlogo.cn/mmbiz/g9QIzpmWFAKRaghHqy8PbH6VmjCzDntLPcLjG8iasHujy7BLuta02pn3tq0SRK7KOqN0yMiabIHjRribetLcbTuFw/0?wx_fmt=png)

* 使用 UIApplicationShortcutItem 类和相关APIs来定义一个动态的快捷方式，然后把定义好的快捷方式赋值给 UIApplication对象的 ShortcutItems 来设置动态的快捷方式。

	以下是代码片段：
	
	swift：
	
	![swift](https://mmbiz.qlogo.cn/mmbiz/g9QIzpmWFAKRaghHqy8PbH6VmjCzDntLibicaiceKSYhvJCcp2fdMBmXUpaaQNWugibm70BkaFK2VKwxt79HdwBoKg/0?wx_fmt=png)
	
	objective-c:
	
	![objective-c](https://mmbiz.qlogo.cn/mmbiz/g9QIzpmWFAKRaghHqy8PbH6VmjCzDntLxokic2KibmwCqY4D4ngFWunIBMptUOdgjqkmUnQfodBxkDjeg2ZJwfuQ/0?wx_fmt=png)
	
	定义好快捷方式之后，系统怎么来处理具体的快捷方式呢？大家想想看，快捷方式是 UIApplication 对象的，UIApplication 对象的事件是由 AppDelegate 对象处理，所以，处理快捷方式 AppDelegate 对象也是有相关的委托方法。
	
	swift：
	
		func application(application: UIApplication, performActionForShortcutItem shortcutItem: UIApplicationShor
tcutItem, completionHandler: (Bool) -> Void)

	objective-c:
	
		-(void)application:(UIApplication *)application performActionForShortcutItem:(UIApplicationShortcutItem *)shortcutItem completionHandler:(void(^)(BOOL succeeded))completionHandler
	
注意：iOS9最多显示四个快捷方式。在这个限制中，系统首先显示静态的快捷方式，假如你的静态的快捷方式不够四个，并且你又定义了动态快捷方式，那么会显示你定义的动态快捷方式。

其次，Peek和Pop。

使用peek和pop交互的过程如下：

1. 表示内容预览可用
2. 显示预览视图，向上扫动弹出快捷方式（peek）
3. 在预览视图的基础上，再用力按压显示详情信息（pop）

app集成peek和pop的时候，需要先检测设备或viewController是否支持3D Touch

swift：

	 if traitCollection.forceTouchCapability == .Available {
                registerForPreviewingWithDelegate(self, sourceView: view)
 }
 
objective-c:

 	if (self.traitCollection.forceTouchCapability == UIForceTouchCapabilityAvailable) {
        [self registerForPreviewingWithDelegate:self sourceView:self.view];
    }
    
然后，当前viewController遵循UIViewControllerPreviewingDelegate协议，实现委托方法：

swift:

	public func previewingContext(previewingContext: UIViewControllerPreviewing, viewControllerForLocation location: CGPoint) -> UIViewController?
public func previewingContext(previewingContext: UIViewControllerPreviewing, commitViewController viewControllerToCommit: UIViewController)

objective-c:

	-(nullable UIViewController *)previewingContext:(id <UIViewControllerPreviewing>)previewingContext viewControllerForLocation:(CGPoint)location 

	-(void)previewingContext:(id <UIViewControllerPreviewing>)previewingContext commitViewController:(UIViewController *)viewControllerToCommit
	
实现预览视图的快捷方式的时候，需要在预览视图对应的viewController中实现下面方法：

swift:

	func previewActionItems() -> [UIPreviewActionItem]
objective-c:

	- (NSArray <id <UIPreviewActionItem>> *)previewActionItems
	
最后，力度属性

我们可以监测用户在屏幕上的按压力度，我们在iPad上素描的时候，可以根据按压的力度，决定线条的粗细程度或则改变视图的背景颜色。

![按压力度](https://mmbiz.qlogo.cn/mmbiz/g9QIzpmWFAKRaghHqy8PbH6VmjCzDntL4WCojMC8suG4sc5yn9YtMicxZIgzDAMtz2gyPmicX4uick6JzNI1NBgww/0?wx_fmt=png)

本文参考文献均来自apple官网，下面是具体demo地址：https://github.com/wjl626nice/3DTouch ，其中内含swift和objective-c两种语言的demo，欢迎大家给我提pr。希望能够帮助到大家，谢谢！