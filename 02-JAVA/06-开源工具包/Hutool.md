Hutool是一个小而全的Java工具类库，通过静态方法封装，降低相关API的学习成本，提高工作效率，使Java拥有函数式语言般的优雅，让Java语言也可以“甜甜的”。

Hutool的设计思想是尽量减少重复的定义，让项目中的util这个package尽量少，总的来说有如下的几个思想：

- 方法优先于对象
  
- 自动识别优于用户定义
  
- 便捷性与灵活性并存
  
- 适配与兼容
  
- 可选依赖原则
  
- 无侵入原则,wuqinru
  

Hutool是一个Java工具包类库，对文件、流、加密解密、转码、正则、线程、XML等JDK方法进行封装，组成各种Util工具类，可以帮助我们提升开发效率。
![img-1dae921a76a8cda2f5f37c179716a7ca](https://raw.githubusercontent.com/sameal153/PicturePool/master/PicturePool/laptop202405061755328.png)

想要使用Hutool的功能，必须要先引入它的依赖，在项目的pom.xml文件中引入：

```xml
<dependency>
    <groupId>cn.hutool</groupId>
    <artifactId>hutool-all</artifactId>
    <version>5.8.26</version>
</dependency>
```

## **1.[Convert]**

在Java开发中我们要面对各种各样的类型转换问题，比如：数组转换成字符串，日期转换成字符串等。

我们需要手写许多代码，或者专门处理异常，比较麻烦。

而Hutool包专门提供了Convert类，我们使用它做类型转换，使用起来非常方便。

数字转换为字符串：

```java
int a = 1;
//aStr为"1"
String aStr = Convert.toStr(a);
```

转换为指定类型数组：

```java
long[] b = {1,2,3,4,5};
//bStr为："[1, 2, 3, 4, 5]"
String bStr = Convert.toStr(b);
```

转换为指定类型数组：

```java
String[] b = { "1", "2", "3", "4" };
//结果为Integer数组
Integer[] intArray = Convert.toIntArray(b);

long[] c = {1,2,3,4,5};
//结果为Integer数组
Integer[] intArray2 = Convert.toIntArray(c);
```

转换为日期对象：

```java
String a = "2017-05-06";
Date value = Convert.toDate(a);
```

转换为集合

```java
Object[] a = {"a", "你", "好", "", 1};
List<?> list = Convert.convert(List.class, a);
//从4.1.11开始可以这么用
List<?> list = Convert.toList(a);
```

## 2.**[DateUtil]**

Java本身对日期时间的支持有限，并且Date和Calendar对象的并存导致各种方法使用混乱和复杂。

通常情况下，我们需要使用SimpleDateFormat类，做时间和字符串类型的转换。

其实Hutool包专门提供了DateUtil类，给我们做时间和日期类型转换的。

### **[2.1 Date和Calendar相互转换]**

```java
//当前时间
Date date = DateUtil.date();
//当前时间
Date date2 = DateUtil.date(Calendar.getInstance());
```

### **[2.2 字符串转日期]**

将字符串转换成Date类型：

```java
String dateStr = "2017-03-01";
Date date = DateUtil.parse(dateStr);
```

自定义时间格式做类型转换：

```java
String dateStr = "2017-03-01";
Date date = DateUtil.parse(dateStr, "yyyy-MM-dd");
```

### **[2.3 格式化日期输出]**

```java
String dateStr = "2017-03-01";
Date date = DateUtil.parse(dateStr);

//结果 2017/03/01
String format = DateUtil.format(date, "yyyy/MM/dd");

//常用格式的格式化，结果：2017-03-01
String formatDate = DateUtil.formatDate(date);

//结果：2017-03-01 00:00:00
String formatDateTime = DateUtil.formatDateTime(date);

//结果：00:00:00
String formatTime = DateUtil.formatTime(date);
```

### **[2.4 开始和结束时间]**

有的时候我们需要获得每天的开始时间、结束时间，每月的开始和结束时间等等，DateUtil也提供了相关方法：

```java
String dateStr = "2017-03-01 22:33:23";
Date date = DateUtil.parse(dateStr);

//一天的开始，结果：2017-03-01 00:00:00
Date beginOfDay = DateUtil.beginOfDay(date);

//一天的结束，结果：2017-03-01 23:59:59
Date endOfDay = DateUtil.endOfDay(date);
```

## **3. [StrUtil]**

这个工具的用处类似于Apache Commons Lang中的StringUtil，常用的方法例如isBlank、isNotBlank、isEmpty、isNotEmpty。

### **[3.1  hasBlank方法]**

就是给定一些字符串，如果一旦有空的就返回true，常用于判断好多字段是否有空的（例如web表单数据）。

这两个方法的区别是hasEmpty只判断是否为null或者空字符串（""），hasBlank则会把不可见字符也算做空，isEmpty和isBlank同理。

### **[3.2 removePrefix方法]**

这两个是去掉字符串的前缀后缀的，例如去个文件名的扩展名啥。

```java
String fileName = StrUtil.removeSuffix("pretty_girl.jpg", ".jpg")  //fileName -> pretty_girl
```

还有忽略大小写的removePrefixIgnoreCase和removeSuffixIgnoreCase都比较实用。

### **[3.3 sub方法]**

不得不提一下这个方法，有人说String有了subString你还写它干啥，我想说subString方法越界啥的都会报异常，而使用StrUtil的sub就不会报错：

```java
String str = "abcdefgh";
String strSub1 = StrUtil.sub(str, 2, 3); //strSub1 -> c
String strSub2 = StrUtil.sub(str, 2, -3); //strSub2 -> cde
String strSub3 = StrUtil.sub(str, 3, 2); //strSub2 -> c
```

### **[3.4 format方法]**

灵感来自slf4j，可以使用字符串模板代替字符串拼接。

```java
String template = "{}爱{}，就像老鼠爱大米";
String str = StrUtil.format(template, "我", "你"); //str -> 我爱你，就像老鼠爱大米
```

## **4 .[ReflectUtil]**

Java的反射机制，可以让语言变得更加灵活，对对象的操作也更加“动态”，因此在某些情况下，反射可以做到事半功倍的效果。Hutool针对Java的反射机制做了工具化封装，封装包括：

- 获取构造方法
- 获取字段
- 获取字段值
- 获取方法
- 执行方法（对象方法和静态方法）

### **[4.1 获取某个类的所有方法]**

```java
Method[] methods = ReflectUtil.getMethods(ExamInfoDict.class);
```

### **[4.2 获取某个类的指定方法]**

```java
Method method = ReflectUtil.getMethod(ExamInfoDict.class, "getId");
```

### **[4.3 构造对象]**

```java
ReflectUtil.newInstance(ExamInfoDict.class);
```

### **[4.4 执行方法]**

```java
class TestClass {
    private int a;

    public int getA() {
        return a;
    }

    public void setA(int a) {
        this.a = a;
    }
}
TestClass testClass = new TestClass();
ReflectUtil.invoke(testClass, "setA", 10);
```

## **5 .[IdUtil]**

在分布式环境中，唯一ID生成应用十分广泛，生成方法也多种多样，Hutool针对一些常用生成策略做了简单封装。

唯一ID生成器的工具类，涵盖了：

- UUID
- ObjectId（MongoDB）
- Snowflake（Twitter）

### **[5.1 UUID]**

UUID全称通用唯一识别码（universally unique identifier），JDK通过java.util.UUID提供了 Leach-Salz 变体的封装。在Hutool中，生成一个UUID字符串方法如下：

```java
//生成的UUID是带-的字符串，类似于：a5c8a5e8-df2b-4706-bea4-08d0939410e3
String uuid = IdUtil.randomUUID();

//生成的是不带-的字符串，类似于：b17f24ff026d40949c85a24f4f375d42
String simpleUUID = IdUtil.simpleUUID();
```

说明 Hutool重写java.util.UUID的逻辑，对应类为cn.hutool.core.lang.UUID，使生成不带-的UUID字符串不再需要做字符替换，性能提升一倍左右。

### **[5.2 ObjectId]**

ObjectId是MongoDB数据库的一种唯一ID生成策略，是UUID version1的变种，详细介绍可见：服务化框架－分布式Unique ID的生成方法一览。

Hutool针对此封装了cn.hutool.core.lang.ObjectId，快捷创建方法为：

```java
//生成类似：5b9e306a4df4f8c54a39fb0c
String id = ObjectId.next();

//方法2：从Hutool-4.1.14开始提供
String id2 = IdUtil.objectId();
```

### **[5.3 Snowflake]**

分布式系统中，有一些需要使用全局唯一ID的场景，有些时候我们希望能使用一种简单一些的ID，并且希望ID能够按照时间有序生成。Twitter的Snowflake 算法就是这种生成器。

使用方法如下：

```java
//参数1为终端ID
//参数2为数据中心ID
Snowflake snowflake = IdUtil.getSnowflake(1, 1);
long id = snowflake.nextId();

//简单使用
long id = IdUtil.getSnowflakeNextId();
String id = snowflake.getSnowflakeNextIdStr();
```

## **6 .[RandomUtil]**

RandomUtil主要针对JDK中Random对象做封装，严格来说，Java产生的随机数都是伪随机数，因此Hutool封装后产生的随机结果也是伪随机结果。不过这种随机结果对于大多数情况已经够用。

RandomUtil.randomInt 获得指定范围内的随机数 例如我们想产生一个`[10, 100)`的随机数，则：

```java
int c = RandomUtil.randomInt(10, 100);
```

RandomUtil.randomBytes 随机bytes，一般用于密码或者salt生成

```java
byte[] c = RandomUtil.randomBytes(10);
```

RandomUtil.randomEle 随机获得列表中的元素。

RandomUtil.randomEleSet 随机获得列表中的一定量的不重复元素，返回Set

```java
Set<Integer> set = RandomUtil.randomEleSet(CollUtil.newArrayList(1, 2, 3, 4, 5, 6), 2);
```

## **7 .[BeanUtil]**

通常Java中对Bean的定义是包含setXXX和getXXX方法的对象，在Hutool中，采取一种简单的判定Bean的方法：是否存在只有一个参数的setXXX方法。

### **[7.1 判断是否为Bean对象]**

BeanUtil.isBean方法根据是否存在只有一个参数的setXXX方法或者public类型的字段来判定是否是一个Bean对象。这样的判定方法主要目的是保证至少有一个setXXX方法用于属性注入。

```java
boolean isBean = BeanUtil.isBean(HashMap.class);//false
```

### **[7.2 Bean转为Map]**

BeanUtil.beanToMap方法则是将一个Bean对象转为Map对象。

```java
SubPerson person = new SubPerson();
person.setAge(14);
person.setOpenid("11213232");
person.setName("测试A11");
person.setSubName("sub名字");

Map<String, Object> map = BeanUtil.beanToMap(person);
```

### **[7.3 Bean转Bean]**

Bean之间的转换主要是相同属性的复制，因此方法名为copyProperties，此方法支持Bean和Map之间的字段复制。

BeanUtil.copyProperties方法同样提供一个CopyOptions参数用于自定义属性复制。

```java
SubPerson p1 = new SubPerson();
p1.setSlow(true);
p1.setName("测试");
p1.setSubName("sub测试");

Map<String, Object> map = MapUtil.newHashMap();
BeanUtil.copyProperties(p1, map);
```

## **8.[JSONUtil]**

JSONUtil是针对JSONObject和JSONArray的静态快捷方法集合。

### **[8.1 JSON字符串创建]**

JSONUtil.toJsonStr可以将任意对象（Bean、Map、集合等）直接转换为JSON字符串。如果对象是有序的Map等对象，则转换后的JSON字符串也是有序的。

```java
SortedMap<Object, Object> sortedMap = new TreeMap<Object, Object>() {
    private static final long serialVersionUID = 1L;
    {
    put("attributes", "a");
    put("b", "b");
    put("c", "c");
}};

JSONUtil.toJsonStr(sortedMap);
```

结果：

```java
{"attributes":"a","b":"b","c":"c"}
```

如果我们想获得格式化后的JSON，则：

```
JSONUtil.toJsonPrettyStr(sortedMap);
```

结果：

```java
{
    "attributes": "a",
    "b": "b",
    "c": "c"
}
```

### **[8.2 JSON字符串解析]**

```java
String html = "{\"name\":\"Something must have been changed since you leave\"}";
JSONObject jsonObject = JSONUtil.parseObj(html);
jsonObject.getStr("name");
```

### **[8.3 XML字符串转换为JSON]**

```java
String s = "<sfzh>123</sfzh><sfz>456</sfz><name>aa</name><gender>1</gender>";
JSONObject json = JSONUtil.parseFromXml(s);

json.get("sfzh");
json.get("name");
```

### **[8.4 JSON转换为XML]**

```java
final JSONObject put = JSONUtil.createObj()
        .set("aaa", "你好")
        .set("键2", "test");

// <aaa>你好</aaa><键2>test</键2>
final String s = JSONUtil.toXmlStr(put);
```

### **[8.5 JSON转Bean]**

我们先定义两个较为复杂的Bean（包含泛型）

```java
@Data
public class ADT {
    private List<String> BookingCode;
}

@Data
public class Price {
    private List<List<ADT>> ADT;
}
String json = "{\"ADT\":[[{\"BookingCode\":[\"N\",\"N\"]}]]}";

Price price = JSONUtil.toBean(json, Price.class);
price.getADT().get(0).get(0).getBookingCode().get(0);
```