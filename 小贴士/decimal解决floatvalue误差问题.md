NSString * str = [@"0.05" floatValue];

str的值可能会是0.04999999999

就算改成double也不行，这个问题就要用更精确的decimal来解决了

1.设置精度

NSDecimalNumberHandler * decimalHandle = [NSDecimalNumberHandler decimalNumberHandlerWithRoundingMode:NSRoundUp scale:2 raiseOnExactness:NO raiseOnOverflow:NO raiseOnUnderflow:NO raiseOnDivideByZero:YES];

其中
