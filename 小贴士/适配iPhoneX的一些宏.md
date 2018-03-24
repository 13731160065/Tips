适配iPhoneX的一些宏
=========================

//是不是iphonex
#define IS_iPhoneX ([UIScreen instancesRespondToSelector:@selector(currentMode)] ? CGSizeEqualToSize(CGSizeMake(1125, 2436), [[UIScreen mainScreen] currentMode].size) : NO)


//适配iphonex的nav高
#define NAVIGATION_HEIGHT_iPhoneX (IS_iPhoneX ? 88.0f : 64.0f)


//带适配iphonex的屏幕高
#define SCREEN_HEIGHT_iPhoneX ([UIScreen mainScreen].bounds.size.height-(IS_iPhoneX ? 33.0f : 0.0f))


//底部安全区高度
#define SCREEN_BOTTOM_SAFEAREA (IS_iPhoneX ? 33.0f : 0.0f)
