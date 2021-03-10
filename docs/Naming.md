# 一、编程规约
##（一）命名风格

### 文件命名

**类**文件<span style="color:red">必须</span>使用`UpperCamelCase`风格，但以下情形例外：DO / BO / DTO / VO / AO / PO等。 
<br><span style="color:green">正例</span>：MarcoPolo / UserDO / XmlService / TcpUdpDeal / TaPromotion 
 <br><span style="color:red">反例</span>：macroPolo / UserDo / XMLService / TCPUDPDeal / TAPromotion （即首字母大写的驼峰）

其他文件（如配置文件：`build.xml`、`.gitignore`、`pom.xml`、`application.properties` 等）建议小写文件名，多个字母拼接建议以中划线 `-` 或下划线 `_`拼接。

<span style="color:green">正例</span>：`v1_create_table.sql`、`product-detail.jsp`

### 包命名

包名必须全部小写，包名统一使用单数形式。

<br><span style="color:green">正例</span>：`com.thoughtworks.app.xxx`
<br>

<span style="color:red">反例</span>：`com.ThoughtWorks.App.xx`



### 变量命名

方法名、参数名、成员变量、局部变量都统一使用`lowerCamelCase`风格，必须遵从驼峰形式。代码中的命名均不能以<strong>下划线或美元符号</strong>开始，也不能以<strong>下划线或美元符号</strong>结束。

<br><span style="color:green">正例</span>：

```java
localValue;
getHttpMessage();
inputUserId;

```

<span style="color:red">反例</span>：`_name / __name / $name / name_ / name$ / name__`



2. 【强制】代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。 
  <br><span style="color:orange">说明</span>：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式也要避免采用，更不要使用首字母缩写。
  <br><span style="color:green">正例</span>：alibaba / taobao / youku / hangzhou 等国际通用的名称，可视同英文。 
  <br><span style="color:red">反例</span>：

  ```java

  DaZhePromotion; // 打折，中英文混合使用

  getPingfenByName(); // 评分，中英文混合使用
  
  int 某变量 = 3;  // 使用中文
  
  String sfz; // 身份证，使用首字母缩写
  
  ```

  
  
4. 【强制】常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。 
  <br><span style="color:green">正例</span>：MAX_STOCK_COUNT 
  <br><span style="color:red">反例</span>：MAX_COUNT 

5. 【强制】抽象类命名使用Abstract或Base开头；异常类命名使用Exception结尾；测试类命名以它要测试的类名开始，以Test结尾。 

6. 【强制】类型与中括号紧挨相连来定义数组。 
   <br><span style="color:green">正例</span>：定义整形数组<code>int[] arrayDemo;</code> 
    <br><span style="color:red">反例</span>：在main参数中，使用<code>String args[]</code>来定义。  

9. 【强制】杜绝完全不规范的缩写，避免望文不知义。 
  <br><span style="color:red">反例</span>：AbstractClass“缩写”命名成AbsClass；condition“缩写”命名成 condi，此类随意缩写严重降低了代码的可阅读性。 

10. 【推荐】为了达到代码自解释的目标，任何自定义编程元素在命名时，使用尽量完整的单词组合来表达其意。 
  <br><span style="color:green">正例</span>：从远程仓库拉取代码的类命名为PullCodeFromRemoteRepository。 
  <br><span style="color:red">反例</span>：变量int a; 的随意命名方式。 

11. 【推荐】接口类中的方法和属性不要加任何修饰符号（public 也不要加），保持代码的简洁性，并加上有效的Javadoc注释。尽量不要在接口里定义变量，如果一定要定义变量，肯定是与接口方法相关，并且是整个应用的基础常量。 
   <br><span style="color:green">正例</span>：接口方法签名void f(); 接口基础常量String COMPANY = "alibaba"; 
   <br><span style="color:red">反例</span>：接口方法定义public abstract void f(); 
   <br><span style="color:orange">说明</span>：JDK8中接口允许有默认实现，那么这个default方法，是对所有实现类都有价值的默认实现。 
   
12. 接口和实现类的命名有两套规则：  
   1）【强制】对于Service和DAO类，基于SOA的理念，暴露出来的服务一定是接口，内部的实现类用Impl的后缀与接口区别。 
   <br><span style="color:green">正例</span>：CacheServiceImpl实现CacheService接口。<br>
   2） 【推荐】 如果是形容能力的接口名称，取对应的形容词为接口名（通常是–able的形式）。
   <br><span style="color:green">正例</span>：AbstractTranslator实现 Translatable。 
   
10. 【参考】枚举类名建议带上Enum后缀，枚举成员名称需要全大写，单词间用下划线隔开。 
  <br><span style="color:orange">说明</span>：枚举其实就是特殊的常量类，且构造方法被默认强制是私有。 
  <br><span style="color:green">正例</span>：枚举名字为ProcessStatusEnum的成员名称：SUCCESS / UNKNOWN_REASON。 

11. 【强制】long或者Long初始赋值时，使用大写的L，不能是小写的l，小写容易跟数字1混淆，造成误解。 
   <br><span style="color:orange">说明</span>：<pre>Long a = 2l;</pre> 写的是数字的`21`，还是Long型的`2`

12. 
### 常量定义

1. 【强制】不允许任何魔法值（即未经预先定义的常量）直接出现在代码中。
<br><span style="color:red">反例</span>：
```
String key = "Id#taobao_" + tradeId;       
cache.put(key, value); 
```
2. 
3. 【推荐】不要使用一个常量类维护所有常量，按常量功能进行归类，分开维护。 
<br><span style="color:orange">说明</span>：大而全的常量类，非得使用查找功能才能定位到修改的常量，不利于理解和维护。 
<br><span style="color:green">正例</span>：缓存相关常量放在类CacheConsts下；系统配置相关常量放在类ConfigConsts下。 
4. 【推荐】常量的复用层次有五层：跨应用共享常量、应用内共享常量、子工程内共享常量、包内共享常量、类内共享常量。  
1） 跨应用共享常量：放置在二方库中，通常是client.jar中的constant目录下。
2） 应用内共享常量：放置在一方库中，通常是子模块中的constant目录下。
<br><span style="color:red">反例</span>：易懂变量也要统一定义成应用内共享常量，两位攻城师在两个类中分别定义了表示“是”的变量：
```
    类A中：public static final String YES = "yes";
    类B中：public static final String YES = "y";
    A.YES.equals(B.YES) 预期是true，但实际返回为false，导致线上问题。
```
3） 子工程内部共享常量：即在当前子工程的constant目录下。  
4） 包内共享常量：即在当前包下单独的constant目录下。  
5） 类内共享常量：直接在类内部private static final定义。 
5. 【推荐】如果变量值仅在一个固定范围内变化用enum类型来定义。 说明：如果存在名称之外的延伸属性使用enum类型，下面正例中的数字就是延伸信息，表示一年中的第几个季节。 
 <br><span style="color:green">正例</span>： 
```
  public enum SeasonEnum {   
          SPRING(1), SUMMER(2), AUTUMN(3), WINTER(4);
          int seq; 
          SeasonEnum(int seq){         
              this.seq = seq;     
          } 
  } 
```