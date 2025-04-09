## 本章专题与脉络

<img src="https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751195.png" alt="第1阶段：Java基本语法-第04章" style="zoom:50%;" />

***

## 1. 认识IntelliJ IDEA
### 1.2 IntelliJ IDEA  介绍

IDEA，全称 `IntelliJ IDEA`，是 Java 语言的集成开发环境，目前已经（基本）`代替`了Eclipse的使用。IDEA 在业界被公认为是最好的 Java 开发工具（之一），因其`功能强悍`、`设置人性化`，而深受Java、大数据、移动端程序员的喜爱。

IntelliJ IDEA 在 2015 年的官网上这样介绍自己：

> Excel at enterprise, mobile and web development with Java, Scala and Groovy,with all the latest modern technologies and frameworks available out of thebox.
>

![image-20221018104714861](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751200.png)

### 1.3 IDEA的主要优势：(vs Eclipse)

**功能强大：**

① 强大的整合能力。比如：Git、Maven、Spring等

<img src="https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751201.png" alt="1576218068631" style="zoom: 67%;" />

② 开箱即用的体验（集成版本控制系统、多语言支持的框架随时可用，无需额外安装插件）

**符合人体工程学：**

① 高度智能（快速的智能代码补全、实时代码分析、可靠的重构工具）

![image-20221018104821144](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751202.png)

② 提示功能的快速、便捷、范围广

![img](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751203.jpg)

![image-20221018104942633](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751204.png)

③ 好用的快捷键和代码模板

④ 精准搜索

### 1.4 IDEA  的下载
- IDEA 分为两个版本： `旗舰版(Ultimate)`和 `社区版(Community)`。


- IDEA的大版本每年迭代一次，大版本下的小版本（如：2022.x）迭代时间不固定，一般每年3个小版本。


![image-20220606191620253](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751205.png)

两个不同版本的详细对比，可以参照官网：
https://www.jetbrains.com/idea/features/editions_comparison_matrix.html

官网提供的详细使用文档：
https://www.jetbrains.com/help/idea/meet-intellij-idea.html

## 3. HelloWorld的实现

### 3.1 新建Project - Class

选择"New Project"：

<img src="https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751232.png" alt="image-20221019174051967" style="zoom:80%;" />

指名工程名、使用的JDK版本等信息。如下所示：

![image-20221019174355370](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751233.png)

接着创建Java类：

![image-20221019174505876](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751234.png)

![image-20221019174551606](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751235.png)

### 3.2 编写代码

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello,World!");
    }
}
```

### 3.3 运行

![image-20221019174716442](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751236.png)

![image-20221019174801370](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751237.png)

## 4. JDK相关设置

### 4.1 项目的JDK设置

`File-->Project Structure...-->Platform Settings -->SDKs`

![image-20221019174847921](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751238.png)

![image-20221019175030852](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751239.png)

- 注1：SDKs全称是Software Development Kit ，这里一定是选择JDK的安装根目录，不是JRE的目录。
- 注2：这里还可以从本地添加多个JDK。使用“+”即可实现。

### 4.2 out目录和编译版本

`File-->Project Structure...-->Project Settings -->Project`

![image-20221019175358200](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751240.png)

## 5. 详细设置

### 5.1 如何打开详细配置界面

1、显示工具栏

![image-20221019175536721](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751241.png)

2、选择详细配置菜单或按钮

![image-20221019175620422](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751242.png)

![image-20221019175953767](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751243.png)

### 5.2 系统设置

#### 1、默认启动项目配置

![image-20221019180050832](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751244.png)

启动IDEA时，默认自动打开上次开发的项目？还是自己选择？

如果去掉Reopen projects on startup前面的对勾，每次启动IDEA就会出现如下界面：

![image-20221019180304644](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751245.png)

#### 2、取消自动更新

Settings-->Appearance & Behavior->System Settings -> Updates

![image-20221019180428323](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751246.png)

默认都打√了，建议检查IDE更新的√去掉，检查插件更新的√选上。

### 5.3 设置整体主题

#### 1、选择主题

![image-20221019180637822](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751247.png)

#### 2、设置菜单和窗口字体和大小

![image-1655136527800](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751248.png)

#### 3、设置IDEA背景图

![image-20221018204241748](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751249.png)

选择一张合适的图片作为背景，即可。

![image-20221018204305159](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751250.png)

### 5.4 设置编辑器主题样式

#### 1、编辑器主题

![image-1655136655026](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751251.png)

#### 2、字体大小

![image-1655136907073](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751252.png)

更详细的字体与颜色如下：

![image-20221019182625234](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751253.png)

> 温馨提示：如果选择某个font字体，中文乱码，可以在fallback font（备选字体）中选择一个支持中文的字体。
>

#### 3、注释的字体颜色

![image-20220616121435182](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751254.png)

- Block comment：修改多行注释的字体颜色
- Doc Comment –> Text：修改文档注释的字体颜色
- Line comment：修改单行注释的字体颜色

### 5.5 显示行号与方法分隔符

![image-1655137441471](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751255.png)

### 5.6 代码智能提示功能

![image-1655137649491](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751256.png)

IntelliJ IDEA 的代码提示和补充功能有一个特性：`区分大小写`。 如果想不区分大小写的话，就把这个对勾去掉。`建议去掉勾选`。

### 5.7 自动导包配置

* 默认需要自己手动导包，Alt+Enter快捷键

![image-1655138308426](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751257.png)

* 自动导包设置
  * 动态导入明确的包：Add unambiguous imports on the fly，该设置具有全局性；
  * 优化动态导入的包：Optimize imports on the fly，该设置只对当前项目有效；

![image-1655138465774](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751258.png)

### 5.8 设置项目文件编码（一定要改）

![image-20220615190832482](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751259.png)

说明： Transparent native-to-ascii conversion主要用于转换ascii，显式原生内容。一般都要勾选。

### 5.9 设置控制台的字符编码

![image-20221019003153265](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751260.png)

### 5.10 修改类头的文档注释信息

![image-20221018114632127](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751262.png)

比如：

```java
/**
* ClassName: ${NAME}
* Package: ${PACKAGE_NAME}
* Description: 
* @Author 尚硅谷-宋红康
* @Create ${DATE} ${TIME} 
* @Version 1.0   
*/
```

常用的预设的变量，这里直接贴出官网给的：

```java
${PACKAGE_NAME} - the name of the target package where the new class or interface will be created. 
${PROJECT_NAME} - the name of the current project. 
${FILE_NAME} - the name of the PHP file that will be created. 
${NAME} - the name of the new file which you specify in the New File dialog box during the file creation. 
${USER} - the login name of the current user. 
${DATE} - the current system date. 
${TIME} - the current system time. 
${YEAR} - the current year. 
${MONTH} - the current month. 
${DAY} - the current day of the month. 
${HOUR} - the current hour. 
${MINUTE} - the current minute. 
${PRODUCT_NAME} - the name of the IDE in which the file will be created. 
${MONTH_NAME_SHORT} - the first 3 letters of the month name. Example: Jan, Feb, etc. 
${MONTH_NAME_FULL} - full name of a month. Example: January, February, etc.

```

### 5.11 设置自动编译

`Settings-->Build,Execution,Deployment-->Compiler`

<img src="https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751263.png" alt="1655109415450" style="zoom: 67%;" />

### 5.12 设置为省电模式 (可忽略)

![image-20220616121851207](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751264.png)

IntelliJ IDEA 有一种叫做省电模式的状态，开启这种模式之后 IntelliJ IDEA 会`关掉代码检查`和`代码提示`等功能。所以一般也可认为这是一种`阅读模式`，如果你在开发过程中遇到突然代码文件不能进行检查和提示，可以来看看这里是否有开启该功能。

### 5.13 取消双击shift搜索

因为我们按shift切换中英文输入方式，经常被按到，总是弹出搜索框，太麻烦了。可以取消它。

<img src="https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751265.png" alt="1659191272699" style="zoom:80%;" />

- 方式1：适用于IDEA 2022.1.2版本

在2022.1版本中，采用如下方式消双击shift出现搜索框：搜索double即可，勾选Disable double modifier key shortcuts，禁用这个选项。

![image-1659190132458](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751266.png)

- 方式2：适用于IDEA 2022.1.2之前版本

双击shift 或 ctrl + shift + a，打开如下搜索窗口：

![image-1577243967254](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751267.png)

选择registry...，找到"ide.suppress.double.click.handler"，把复选框打上勾就可以取消双击shift出现搜索框了。

![image-1577244045320](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751268.png)

## 6. 工程与模块管理

### 6.1 IDEA项目结构

**层级关系：**

```
project(工程) - module(模块) - package(包) - class(类)
```

**具体的：**
#IDEA结构

```
一个project中可以创建多个module

一个module中可以创建多个package

一个package中可以创建多个class
```

> 这些结构的划分，是为了方便管理功能代码。

### 6.2 Project和Module的概念

在 IntelliJ IDEA 中，提出了Project和Module这两个概念。

<img src="https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751269.png" alt="image-20220523014358169" style="zoom:80%;" />

在 IntelliJ IDEA 中Project是`最顶级的结构单元`，然后就是Module。目前，主流的大型项目结构基本都是多Module的结构，这类项目一般是`按功能划分`的，比如：user-core-module、user-facade-module和user-hessian-module等等，模块之间彼此可以`相互依赖`，有着不可分割的业务关系。因此，对于一个Project来说：

- 当为单Module项目的时候，这个单独的Module实际上就是一个Project。
- 当为多Module项目的时候，多个模块处于同一个Project之中，此时彼此之间具有`互相依赖`的关联关系。
- 当然多个模块没有建立依赖关系的话，也可以作为单独一个“小项目”运行。

### 6.3 Module和Package

在一个module下，可以声明多个包（package），一般命名规范如下：

```
1.不要有中文
2.不要以数字开头
3.给包取名时一般都是公司域名倒着写,而且都是小写
  比如：尚硅谷网址是www.atguigu.com
  那么我们的package包名应该写成：com.atguigu.子名字。
```

### 6.4 创建Module

建议创建“Empty空工程”，然后创建多模块，每一个模块可以独立运行，相当于一个小项目。JavaSE阶段不涉及到模块之间的依赖。后期再学习模块之间的依赖。

步骤：

（1）选择创建模块

![image-1655167625885](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751270.png)

（2）选择模块类型：这里选择创建Java模块，给模块命名，确定存放位置

![image-1659191966074](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751271.png)

（4）模块声明在工程下面

![image-1659192028623](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751272.png)

### 6.5 删除模块

（1）移除模块

![image-1659192150052](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751273.png)

![image-1659192180062](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751274.png)

（2）彻底删除模块

![image-1659192241224](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751275.png)

### 6.6 导入老师的模块

（1）将老师的模块`teacher_chapter04`整个的复制到自己IDEA项目的路径下

![image-1659192514219](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751276.png)

接着打开自己IDEA的项目，会在项目目录下看到拷贝过来的module，只不过不是以模块的方式呈现。

![image-1659192692658](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751277.png)

（2）查看Project Structure，选择import module

![image-20220615213827271](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751278.png)

![image-20220615214746952](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751279.png)

（3）选择要导入的module：

![image-1659192850055](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751280.png)

![image-20220615214916374](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751281.png)

（4）接着可以一路Next下去，最后选择Overwrite

![image-1659192928140](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751282.png)

![image-1659192995900](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751283.png)

最后点击OK即可了。

### 6.7 同时打开两个IDEA项目工程

#### 1、两个IDEA项目工程效果

有些同学想要把上课练习代码和作业代码分开两个IDEA项目工程。

![image-20211229111753237](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751284.png)

![image-20211229111906342](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751285.png)

#### 2、新建一个IDEA项目

注意：第一次需要新建，之后直接打开项目工程即可

![image-1655170522054](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751286.png)

![image-1655170341953](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751287.png)

![image-1655170765902](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751288.png)

#### 3、打开两个IDEA项目

![image-20211229112314671](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751289.png)

![image-20211229112343470](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751290.png)

![image-1655173351720](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751291.png)

### 6.8 导入前几章非IDEA工程代码

**1、创建chapter01、chapter02、chapter03等章节的module**

将相应章节的源文件粘贴到module的src下。

![image-20220615220728669](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751292.png)

![image-20220615220755529](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751293.png)

打开其中各个源文件，会发现有乱码。比如：

![image-20220615220846097](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751294.png)

**2、设置编码**

当前项目是UTF-8。如果原来的.java文件都是GBK的（如果原来.java文件有的是GBK，有的是UTF-8就比较麻烦了）。

可以单独把这两个模块设置为GBK编码的。

![image-20220615220544760](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751295.png)

改为GBK，确认即可。如图：

![image-20220615220950214](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751296.png)

## 7. 代码模板的使用

### 7.1 查看Postfix Completion模板(后缀补全)

![image-1655173712802](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751297.png)

### 7.2 查看Live Templates模板(实时模板)

![img](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751298.jpg)

### 7.3 常用代码模板

#### 1、非空判断

* 变量.null：if(变量 == null)
* 变量.nn：if(变量 != null) 
* 变量.notnull：if(变量 != null) 
* ifn：if(xx  == null)
* inn：if(xx  != null)

#### 2、遍历数组和集合

* 数组或集合变量.fori：for循环
* 数组或集合变量.for：增强for循环
* 数组或集合变量.forr：反向for循环
* 数组或集合变量.iter：增强for循环遍历数组或集合

#### 3、输出语句

- sout：相当于System.out.println
- soutm：打印当前方法的名称
- soutp：打印当前方法的形参及形参对应的实参值
- soutv：打印方法中声明的最近的变量的值
- 变量.sout：打印当前变量值
- 变量.soutv：打印当前变量名及变量值

#### 4、对象操作

- 创建对象
  - Xxx.new  .var ：创建Xxx类的对象，并赋给相应的变量
  - Xxx.new  .field：会将方法内刚创建的Xxx对象抽取为一个属性
- 强转
  - 对象.cast：将对象进行强转
  - 对象.castvar：将对象强转后，并赋给一个变量

#### 5、静态常量声明

* psf：public static final
* psfi：public static final int
* psfs：public static final String
* prsf：private static final

### 7.4 自定义代码模板

#### 7.4.1 自定义后缀补全模板

![image-20221018143204667](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751299.png)

![image-20221018143606913](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751300.png)

#### 7.4.2 自定义Live Templates

例如：定义sop代表System.out.print();语句

①在Live Templates中增加模板

![image-1576467339631](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751301.png)

②先定义一个模板的组，这样方便管理所有自定义的代码模板

![image-1576467395084](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751302.png)

③在模板组里新建模板

![image-1576467478993](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751303.png)

④定义模板（以输出语句为例）

![image-1576467712251](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751304.png)

- Abbreviation：模板的缩略名称
- Description：模板的描述
- Template text：模板的代码片段
- 模板应用范围。比如点击Define。选择如下：应用在java代码中。

![image-1576467768103](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751305.png)

**其它模板1：单元测试模板：**

```java
@Test
public void test$var1$(){
    $var2$
}
```

![image-20220612124137427](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751306.png)

**其它模板2：创建多线程**

```java
new Thread(){
    public void run(){
        $var$
    }
};
```

![image-20220612124221967](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751307.png)

**其它模板3：冒泡排序**

```java
for(int $INDEX$ = 1; $INDEX$ < $ARRAY$.length; $INDEX$++) {
    for(int $INDEX2$ = 0; $INDEX2$ < $ARRAY$.length-$INDEX$; $INDEX2$++) {
        if($ARRAY$[$INDEX2$] > $ARRAY$[$INDEX2$+1]){
            $ELEMENT_TYPE$ temp = $ARRAY$[$INDEX2$];
            $ARRAY$[$INDEX2$] = $ARRAY$[$INDEX2$+1];
            $ARRAY$[$INDEX2$+1] = temp;
        }
    }
}
```

![image-20220612124541378](https://raw.githubusercontent.com/sameal153/PicturePool/master/img/202311111751308.png)


## 8-IDEA的日常快捷键

### 第1组：通用型

|说明|快捷键|
|---|---|
|复制代码-copy|ctrl + c|
|粘贴-paste|ctrl + v|
|剪切-cut|ctrl + x|
|撤销-undo|ctrl + z|
|反撤销-redo|ctrl + shift + z|
|保存-save all|ctrl + s|
|全选-select all|ctrl + a|

### 第2组：提高编写速度（上）

|说明|快捷键|
|---|---|
|智能提示-edit|alt + enter|
|提示代码模板-insert live template|ctrl+j|
|使用xx块环绕-surround with ...|ctrl+alt+t|
|调出生成getter/setter/构造器等结构-generate ...|alt+insert|
|自动生成返回值变量-introduce variable ...|ctrl+alt+v|
|复制指定行的代码-duplicate line or selection|ctrl+d|
|删除指定行的代码-delete line|ctrl+y|
|切换到下一行代码空位-start new line|shift + enter|
|切换到上一行代码空位-start new line before current|ctrl +alt+ enter|
|向上移动代码-move statement up|ctrl+shift+↑|
|向下移动代码-move statement down|ctrl+shift+↓|
|向上移动一行-move line up|alt+shift+↑|
|向下移动一行-move line down|alt+shift+↓|
|方法的形参列表提醒-parameter info|ctrl+p|

### 第3组：提高编写速度（下）

|说明|快捷键|
|---|---|
|批量修改指定的变量名、方法名、类名等-rename|shift+f6|
|抽取代码重构方法-extract method ...|ctrl+alt+m|
|重写父类的方法-override methods ...|ctrl+o|
|实现接口的方法-implements methods ...|ctrl+i|
|选中的结构的大小写的切换-toggle case|ctrl+shift+u|
|批量导包-optimize imports|ctrl+alt+o|

### 第4组：类结构、查找和查看源码

|说明|快捷键|
|---|---|
|如何查看源码-go to class...|ctrl + 选中指定的结构 或 ctrl+n|
|显示当前类结构，支持搜索指定的方法、属性等-file structure|ctrl+f12|
|退回到前一个编辑的页面-back|ctrl+alt+←|
|进入到下一个编辑的页面-forward|ctrl+alt+→|
|打开的类文件之间切换-select previous/next tab|alt+←/→|
|光标选中指定的类，查看继承树结构-Type Hierarchy|ctrl+h|
|查看方法文档-quick documentation|ctrl+q|
|类的UML关系图-show uml popup|ctrl+alt+u|
|定位某行-go to line/column|ctrl+g|
|回溯变量或方法的来源-go to implementation(s)|ctrl+alt+b|
|折叠方法实现-collapse all|ctrl+shift+ -|
|展开方法实现-expand all|ctrl+shift+ +|

### 第5组：查找、替换与关闭

|说明|快捷键|
|---|---|
|查找指定的结构|ctlr+f|
|快速查找：选中的Word快速定位到下一个-find next|ctrl+l|
|查找与替换-replace|ctrl+r|
|直接定位到当前行的首位-move caret to line start|home|
|直接定位到当前行的末位 -move caret to line end|end|
|查询当前元素在当前文件中的引用，然后按 F3 可以选择|ctrl+f7|
|全项目搜索文本-find in path ...|ctrl+shift+f|
|关闭当前窗口-close|ctrl+f4|

### 第6组：调整格式

|说明|快捷键|
|---|---|
|格式化代码-reformat code|ctrl+alt+l|
|使用单行注释-comment with line comment|ctrl + /|
|使用/取消多行注释-comment with block comment|ctrl + shift + /|
|选中数行，整体往后移动-tab|tab|
|选中数行，整体往前移动-prev tab|shift + tab|

## 9-Debug快捷键

|说明|快捷键|
|---|---|
|单步调试（不进入函数内部）- step over|F8|
|单步调试（进入函数内部）- step into|F7|
|强制单步调试（进入函数内部） - force step into|alt+shift+f7|
|选择要进入的函数 - smart step into|shift + F7|
|跳出函数 - step out|shift + F8|
|运行到断点 - run to cursor|alt + F9|
|继续执行，进入下一个断点或执行完程序 - resume program|F9|
|停止 - stop|Ctrl+F2|
|查看断点 - view breakpoints|Ctrl+Shift+F8|
|关闭 - close|Ctrl+F4|

