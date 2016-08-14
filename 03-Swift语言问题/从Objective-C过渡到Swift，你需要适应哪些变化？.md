从Objective-C过渡到Swift，你需要适应哪些变化？
-----
date: 2016-07-13 00:24:20

作者：[卢静](https://github.com/orgs/HNQingyun/people/lujing666208)

最近一段时间研究了swift,swift语言相对OC而言，语法更简洁、快速、安全，符合现代化编程思维，同时扩展了很多很强大的特性，比如类型推断、函数式编程、泛型等。但就做项目而言，用swift开发较之OC，大体只需要适应两个变化：语法的不同和第三方框架的不同。关于基本语法的教程，网上都有很多资料。需要详细了解请点击[这里](http://wiki.jikexueyuan.com/project/swift/chapter2/chapter2.html)。如果基本语法已经看过，那么下面的总结应该可以帮助你更好的理解，以便快速上手swift开发。
#### 一、常用基本知识点归纳
 1. 注意运算符使用时，要么前后都有空格，要么都没空格。否则会报错（认为运算符是前缀或者后缀），如 let x =5 编译报错。
 2. 代码标注使用//MARK:- xxx (`对比OC的#pragma mark - xxx`)<!--more-->
 3. swift不支持#define宏定义，简单宏请使用let定义常量，复杂宏需要实现函数
 4. 表示值缺失使用可选类型：Type?,表示要么没有值，要么有一个Type类型的值(不可能出现其他类型的值) (`对比OC的nil只能表示空对象，不能表示任何类型的值缺失`)
 5. 类型转换使用as?或者as!,如AnyObject as? String(`对比OC的强制转换：NSString *str = xxx`)
 6. 获取某个类的类型使用：类名.self(`对比OC的[类名 class]`)
 7. 获取类名的字符串使用：String(类名)（`对比OC的NSStringFromClass([类名 class])`）
 8. 重写setter方法使用属性观察器didSet（`对比OC的直接自定义setter方法`）
 9. 某些特性的枚举值需要做或运算时使用[值1,值2]完成 (`对比OC的或运算：值1|值2`) 
 10. swift2.2之前selector直接使用"方法名"，之后使用#selector(方法名)（`对比OC的@selector()`）
 11. 子类重写父类的属性和方法必须使用override关键字
 12. 自定义打印对象需要重写description属性:override var description:String{}(`对比OC的重写description方法`)
 13. 类型方法使用static/class关键字来区分于实例方法，其中static修饰的类方法不可以被子类重写，class修饰的可以。(`对比OC的类方法/实例方法：+/-`)
 14. swift表示只读属性，使用常量属性：let xxx:Type (`对比OC的readonly属性`) 
 15. swift计算型属性不占内存，仅提供getter/setter,用于间接获取或设置其他属性的值。(`对比OC的dynamic关键字修饰的属性`)
 16. swift调用构造器生成实例：类型名()/类型名(xx:xxx,yy:yyy,...)(`对比OC的[[类名 alloc] init]或者[[类名 alloc] initWithXx:xxx Yy:yyy ...]`)
 17. swift懒加载使用lazy属性：lazy var xxx:Type = {//具体操作}() (`对比OC的 - (Type)xxx{if (xxx == nil){//具体操作} return xxx}`)
 18. swift单行单例：
 
 	```
 	class Singleton:NSObject{
 		static let shareInstance = Singleton()//可以确保多线程时，也只创建一次
 		private override init(){}//设置为私有，避免在外部创建实例
 	}
 	
 	//外部使用
 	let instance = Singleton.shareInstance
 	
 	``` 
 19. swift中如果要定义类别，可使用扩展extension：extension 类型名{//可以扩展计算型属性和方法}(`对比OC的@interface 类型名(类别名)`)
 20. swift类必须继承自NSObject才可以在OC的代码中调用

#### 二、swift优秀第三方库推荐
1. Alamofire：著名的AFNetworking网络基础库Swift版[github地址](https://github.com/Alamofire/Alamofire.git),`类似OC中的AFNetworking`
2. SwiftyJSON：最为开发者认可的JSON解析类[github地址](https://github.com/SwiftyJSON/SwiftyJSON.git),`类似OC中的JSONKit`
3. Kingfisher：图片下载和缓存处理的库[github地址](https://github.com/onevcat/Kingfisher.git),`类似OC中的SDWebImage`
4. SnapKit：自动布局的库[github地址](https://github.com/SnapKit/SnapKit.git),`类似OC中的Masonry`
5. SQLite.swift：简单、轻量，使用上最SQL的SQLite封装库[github地址](https://github.com/stephencelis/SQLite.swift.git),`类似OC中的FMDB`
6. SugarRecord：基于CoreData与REALM的好用封装[github地址](https://github.com/pepibumur/SugarRecord.git)
7. SweetAlert：带动画效果弹窗封装类[github地址](https://github.com/codestergit/SweetAlert-iOS.git)
8. RAMAnimatedTabBarController：灵动的动画标签栏类库[github地址](https://github.com/Ramotion/animated-tab-bar.git)
9. PNChart-Swift：带动画效果的图表控件库[github地址](https://github.com/kevinzhow/PNChart-Swift.git)
10. LTMorphingLabel：各种文字动画效果[github地址](https://github.com/lexrus/LTMorphingLabel.git)

PS：如果没有所需的swift版本第三方库，可以使用桥接头文件的方式继续使用OC的相应的第三方库。

最后，希望这篇文章对你有所帮助，可以早日掌握swift这门新语言。
