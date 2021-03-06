# NSBundle+changeBundleId.h文件

```
//
//  NSBundle+changeBundleId.h
//  fff3
//
//  Created by 王泽众 on 2018/3/22.
//  Copyright © 2018年 王泽众. All rights reserved.
//

#import <Foundation/Foundation.h>

@interface NSBundle (changeBundleId)

/**
 修改包名

 @param bundleId 包名，nil为默认包名
 */
- (void)changeBundleIdentifier:(NSString *)bundleId;

@end
```

# NSBundle+changeBundleId.m文件

```
//
//  NSBundle+changeBundleId.m
//  fff3
//
//  Created by 王泽众 on 2018/3/22.
//  Copyright © 2018年 王泽众. All rights reserved.
//

#import "NSBundle+changeBundleId.h"
#import <objc/runtime.h>

//原包名
#define NSBundle_changeBundleIdentifier_orgBundleId @"NSBundle_changeBundleIdentifier_orgBundleId"

//修改包名
#define NSBundle_changeBundleIdentifier_nowBundleId @"NSBundle_changeBundleIdentifier_nowBundleId"

@implementation NSBundle (changeBundleId)

//修改包名
- (void)changeBundleIdentifier:(NSString *)bundleId {
    NSUserDefaults * def = [NSUserDefaults standardUserDefaults];
    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{
        [def setObject:[[NSBundle mainBundle] bundleIdentifier] forKey:NSBundle_changeBundleIdentifier_orgBundleId];
        [def synchronize];
        
        Method m1 = class_getInstanceMethod([self class], NSSelectorFromString(@"bundleIdentifier"));
        Method m2 = class_getInstanceMethod([self class], NSSelectorFromString(@"_changeB"));
        method_exchangeImplementations(m1, m2);
    });
    if (bundleId) {
        [def setObject:bundleId forKey:NSBundle_changeBundleIdentifier_nowBundleId];
        [def synchronize];
    } else {
        [def setObject:[def objectForKey:NSBundle_changeBundleIdentifier_orgBundleId] forKey:NSBundle_changeBundleIdentifier_nowBundleId];
        [def synchronize];
    }
}

- (NSString *)_changeB {
    return [[NSUserDefaults standardUserDefaults] objectForKey:NSBundle_changeBundleIdentifier_nowBundleId];
}

@end
```
