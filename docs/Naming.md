##命名规范

任何傻瓜都能够编写出计算机可以理解的代码，但只有优秀的程序员能够编 写出人类可以理解的代码。——Kent Beck





### 文件命名

**类**文件<span style="color:red">必须</span>使用`UpperCamelCase`风格，异常类命名使用Exception结尾；测试类命名以它要测试的类名开始，以Test结尾；枚举类名建议带上Enum后缀，枚举成员名称需要全大写，单词间用下划线隔开。 但以下情形例外：DO / BO / DTO / VO / AO / PO等。 
<br><span style="color:green">正例</span>：

```shell
MarcoPolo.java
UserDO.java
XmlService.java
TcpUdpDeal.java
TaPromotion.java
SignException.java
SignTest.java
UserEnum.java
```

 <br><span style="color:red">反例</span>：macroPolo / UserDo / XMLService / TCPUDPDeal / TAPromotion （即首字母大写的大驼峰）

其他文件（如配置文件：`build.xml`、`.gitignore`、`pom.xml`、`application.properties` 等）建议小写文件名，多个字母拼接建议以中划线 `-` 或下划线 `_`拼接。

<span style="color:green">正例</span>：`v1_create_table.sql`、`product-detail.jsp`




### 包命名

包名必须全部小写，包名统一使用单数形式。

<br><span style="color:green">正例</span>：`com.thoughtworks.app.xxx`
<br>

<span style="color:red">反例</span>：`com.ThoughtWorks.App.xx`



### 变量命名

1. 方法名、参数名、成员变量、局部变量都统一使用`lowerCamelCase`风格。代码中的命名均不能以<strong>下划线或美元符号</strong>开始，也不能以<strong>下划线或美元符号</strong>结束。只有**单元测试的函数名例外**。

  <br><span style="color:green">正例</span>：

  ```java
  localValue;
  getHttpMessage();
  inputUserId;

  ```

  <span style="color:red">反例</span>：`_name / __name / $name / name_ / name$ / name__`
  
  单元测试函数名，在 java 中只有单元测试是这样描述函数名的
  
  ```java
  public void given_a_is_1_b_is_2_when_called_add_then_return_3() {
    
  }
  ```
  
  

​			

2. 代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。 任何自定义编程元素在命名时，使用尽量完整的单词组合来表达其意。 
  <br><span style="color:orange">说明</span>：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式也要避免采用，更不要使用首字母缩写，此类随意缩写严重降低了代码的可阅读性。 
  <br><span style="color:green">正例</span>：alibaba / taobao / youku / hangzhou 等国际通用的名称，可视同英文。 
  <br><span style="color:red">反例</span>：

  ```java

  DaZhePromotion; // 打折，中英文混合使用

  getPingfenByName(); // 评分，中英文混合使用
  
  int 某变量 = 3;  // 使用中文
  
  String sfz; // 身份证，使用首字母缩写
  
  ```

  
  
  
  
4. long或者Long初始赋值时，使用大写的L，不能是小写的l，小写容易跟数字1混淆，造成误解。 
  <br><span style="color:orange">说明</span>：<pre>Long a = 2l;</pre> 写的是数字的`21`，还是Long型的`2`

  

### 常量定义

1. 常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。 也可使用枚举对象将业务常量封装在一个功能模块中。
   <br><span style="color:green">正例</span>：MAX_STOCK_COUNT 
   
   <span style="color:green">正例</span>：枚举名字为 `ProcessStatusEnum` 的成员名称：`SUCCESS` / `UNKNOWN_REASON`。 
   
2. <br><span style="color:red">反例</span>：MAX_COUNT 


2. 常量命名要有业务意义，而非英文直译。
  
   <span style="color:green">正例</span>：`String MAX_STOCK_COUNT = 5;`
   
   <span style="color:red">反例</span>：`String FIVE = 5;`
   
3. 不建议任何魔法值（即未经预先定义的常量）直接出现在代码中。
   <br><span style="color:red">反例</span>：

    ```java
    String key = "Id#" + tradeId; // Id# 为魔法值
    cache.put(key, value); 
    ```

4. 不要使用一个常量类维护所有常量，按常量功能进行归类，分开维护。 
  <br><span style="color:orange">说明</span>：大而全的常量类，非得使用查找功能才能定位到修改的常量，不利于理解和维护。 
  <br><span style="color:green">正例</span>：缓存相关常量放在类CacheConsts下；系统配置相关常量放在类ConfigConsts下。 

5. 
