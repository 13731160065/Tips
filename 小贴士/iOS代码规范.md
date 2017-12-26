代码外
---------------------

**一、文件**

1.文件名、类名以编写者姓名大写首字母开头

例如:

`WZZHomeVC.h`

`WZZHomeVC.m`

2.文件名、类名用纯英文或纯拼音表示

例如:

`WZZHomeViewController.h`

`WZZPhoneNumberHandler.h`

`WZZDaiJiKaVC.h`

**二、文件夹**

1.文件夹名用中文表示，名字贴切，和物理文件名一致。建议在文件夹中创建完再把文件夹拖进来

2.文件夹结构，页面部分使用MVC模式分文件夹，分类从大分类到小分类到具体某个页面的MVC文件夹

例如:

![mvc](https://github.com/13731160065/Tips/raw/master/images/代码规范/mvc.png)

代码中
---------------------

**一、头部文件**

1.同一类的放一起，import的放一起，define放一起，const放一起，中间以换行隔开

2.宏定义用大写英文如果多个单词用下划线分割，局部宏定义用该类名加下划线加名称来定义，防止宏定义的重复

3.宏定义数值对其

例如:

![import](https://github.com/13731160065/Tips/raw/master/images/代码规范/import.png)

**二、注释**

1..m中自定义的方法要加普通注释，.h中的变量和方法都要加**文档注释**

2.参数过长回车换行

3.参数名都写在注释中
			 
4.网络解析中的类型要在代码注释中写清楚功能

见以下示例：

![注释](https://github.com/13731160065/Tips/raw/master/images/代码规范/zhushi.png)

5.有限数量状态的类型要用枚举来表示，不要用字符串比对或01234来定义值

**三、代码编写**

1.自造字典、数组用换行分开每个元素

2.参数名、变量名首字母小写，遵循驼峰命名原则，用英文，见名知意，尽量使用有意义的英文名称（杜绝使用cell1，cell2，cell3）

例如:
 
UIImage * aBigImage;

NSString * aImageNameString;

3.category方法名用**自己名字首字母小写加下划线**开头

例如:

**sd_**setImageWithURL

4.功能不同的代码块必须用换行分开

5.同一类的方法放到一起，不同类之间用#pragma mark - 分开（#pragma mark - 点击事件，加－和不加－是有区别的，注意使用时的区别）

6.相同功能代码放在一起，不同功能代码加回车隔开，不要加太多回车，代码编写要紧密并且分段清晰，不要频繁回车换行

![正确代码块](https://github.com/13731160065/Tips/raw/master/images/代码规范/codeblockyes.png)
![错误代码块](https://github.com/13731160065/Tips/raw/master/images/代码规范/codeblockno.png)

7.定义方法，写语句时注意代码格式，变量、方法、保留字及代码之间用空格分隔，参数与变量之间不需要用空格分隔

![代码编写](https://github.com/13731160065/Tips/raw/master/images/代码规范/func.png)
![代码编写](https://github.com/13731160065/Tips/raw/master/images/代码规范/if.png)
![代码编写](https://github.com/13731160065/Tips/raw/master/images/代码规范/for.png)
![代码编写](https://github.com/13731160065/Tips/raw/master/images/代码规范/while.png)

8.运算符中，==、<、>、&&、||之间用空格分隔，普通运算符之间不用分隔，处理逻辑运算时多加括号使逻辑判断的优先级更清晰

![运算符](https://github.com/13731160065/Tips/raw/master/images/代码规范/opop.png)

9.写方法时需要以以下格式，-或+后边加一个空格，方法名以小写字母开头

- (void)abc:(NSString *)str1 bcd:(NSString *)str2;

10.单例获取实例方法需要以share、default开头

11.xib一定要做好屏幕适配，不要全部固定宽高

12.布xib布局时采用从下层到上层逐层布视图，不能所有视图一路排下来，便于修改

**四、BUG和崩溃**

1.写block和调用option类型的代理方法时，一定要判断方法是否实现，如果没实现直接调用会引起崩溃

2.可变字典用dic[@"key"] = value;的形式赋值，可以避免崩溃，使用setobject的方式会造成程序崩溃

3.无符号类型字段中0-1会变成一个很大的数，使array.count-1时需要注意，不可以直接使用，必须做类型转换，或用可为负的数据类型接收

4.处理视频和多长图片的时候需要注意，尽量使用读取本地的方式读取数据，过大的视频或图片直接加载到内存中会导致内存溢出

**五、全局性**

1.将网络请求解析数据的功能封装到一个单独类中，并且在网络请求类之上再进行一层封装以备后用

2.NSUserDefault的key使用宏定义，可以全局统一放在一个文件中以避免重复

3.非特殊情况**不要用单例、存本地、通知的方式传值**，尽量多用正向赋值、block和代理，使用单例、本地、通知的方式赋值极难查错，使用正向赋值、block、代理可以根据调用查找。

**六、其他**

暂无
