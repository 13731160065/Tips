NSString * str = [@"0.05" floatValue];

str的值可能会是0.04999999999

就算改成double也不行，这个问题就要用更精确的decimal来解决了

**用法**

加 decimalNumberByAdding

减 decimalNumberBySubtracting

乘 decimalNumberByMultiplyingBy

除 decimalNumberByDividingBy

乘方 decimalNumberByRaisingToPower

指数运算 decimalNumberByMultiplyingByPowerOf10

四舍五入 decimalNumberByRoundingAccordingToBehavior

比较 compare

**设置精度**

decimal每一个计算之后可以跟一个叫做withBehavior的东西，就是精度的设置

NSDecimalNumberHandler * decimalHandle = [NSDecimalNumberHandler decimalNumberHandlerWithRoundingMode:NSRoundUp scale:2 raiseOnExactness:NO raiseOnOverflow:NO raiseOnUnderflow:NO raiseOnDivideByZero:YES];

其中roundingMode是一个枚举

// Rounding policies :

数据对比

value    1.2  1.21  1.25  1.35  1.27

Plain    1.2  1.2   1.3   1.4   1.3

Down     1.2  1.2   1.2   1.3   1.2

Up       1.2  1.3   1.3   1.4   1.3

Bankers  1.2  1.2   1.2   1.4   1.3

typedef NS_ENUM(NSUInteger, NSRoundingMode) {

    NSRoundPlain,   // Round up on a tie 四舍五入
    
    NSRoundDown,    // Always down == truncate 直接舍
    
    NSRoundUp,      // Always up 直接入
    
    NSRoundBankers  // on a tie round so last digit is even 也是四舍五入但位数有所不同
    
};
