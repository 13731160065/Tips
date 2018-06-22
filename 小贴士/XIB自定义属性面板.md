# XIB自定义属性面板

用xib时经常用到右侧attributes inspector栏来修改xib的属性，比如一个button一个label，设置文字、字体之类的，有时候就想能不能像u3d一样，直接把我自定义的属性暴露出来呢，用过IQKeyboard的TextView扩展的placeholder以后我惊奇的发现他实现了这一功能，于是我从网上寻找了一下，确实可以实现，而且非常简单。下面就进入正题。

## 1.自定义属性面板

只需在类的@interface上方声明一个IB_DESIGNABLE`(可以实时渲染)`，然后在你要暴露在xib中的属性前边声明一个IBInspectable`(可以显示属性)`即可实现。大概是下边这样的

```

IB_DESIGNABLE
@interface WZZImageCodeAlertView : UIView

@property (nonatomic, assign) IBInspectable CGFloat abc;

@end

```

这时候再去xib的属性界面，就可以看到这个类多了一个abc属性了。

## 2.实时渲染效果

加了属性还不够，修改属性看不到效果不太爽，其实在视图的drawRect方法里修改属性对应的值即可
