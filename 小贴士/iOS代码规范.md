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

1.同一类的放一起，import的放一起，define放一起，const放一起，中间以逗号隔开

2.宏定义用大写英文如果多个单词用下划线分割，局部宏定义用该类名加下划线加名称来定义，防止宏定义的重复

3.宏定义数值对其

例如:

![import](https://github.com/13731160065/Tips/raw/master/images/代码规范/import.png)

**二、注释**

1..m中自定义的方法要加普通注释，.h中的变量和方法都要加**文档注释**

2.参数过长回车换行

3.参数名都写在注释中

4.见以下示例：

/**
\
	辅导师列表接口

	@param categoryId 擅长分类Id

	@param level      级别：1辅导师 2专家

	@param sex        性别：1男 0女
 
 */
 
+ (void)httpGetTutorListCateoryId:(NSString*)categoryId
\
		       withLevel:(NSString*)level
		       \
		         withSex:(NSString*)sex
			 
5.网络解析中的类型要在代码注释中写清楚功能

  例如接口中有一个type:
 
  /**
  	type:
  
  	1.商家 
  
 	2.个人
	
	*/

9.有限数量状态的类型要用枚举来表示，不要用字符串比对或01234来定义值

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

四、全局性

1.将网络请求解析数据的功能封装到一个单独类中，并且在网络请求类之上再进行一层封装以备后用

2.NSUserDefault的key使用宏定义，全局统一放在一个文件中以避免重复

3.非特殊情况**不要用单例、存本地、通知的方式传值**，尽量多用正向赋值、block和代理。

五、其他
暂无
