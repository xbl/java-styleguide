## 条件控制语句 

###  If 语句

1. 表达异常的分支时，尽量使用“短路”方式，少用 if-else，这种方式可以改写成： 
  ```java
  if (condition) {              
  	...              
  	return obj;    
  }   
  // 接着写else的业务逻辑代码; 
  ```
  <br><span style="color:orange">说明</span>：如果非得使用if()...else if()...else...方式表达逻辑，避免后续代码维护困难，请勿超过3层。
  <br><span style="color:green">正例</span>：超过3层的 if-else 的逻辑判断代码可以使用卫语句、策略模式、状态模式等来实现，其中卫语句示例如下： 

  ```java
  public void today() {      
    if (isBusy()) {   
        System.out.println("change time.");
        return; 
    }       
    if (isFree()) {  
        System.out.println("go to travel.");             
        return;     
    }  
    System.out.println("stay at home to learn Alibaba Java Coding Guidelines.");
    return; 
  } 
  ```

  
  
3. 在if/else/for/while/do语句中必须使用大括号。即使只有一行代码，避免采用单行的编码方式：

  <span style="color:green">正例</span>：

  ```java
  if (condition) {
    return something;
  }
  ```

  <span style="color:red">反例</span>：

  ```java
if (condition) return something;
  ```
  
3. 【推荐】使用 `isEmpty(user)` 、`isAdmin(user)` 工具函数封装判断条件，以提高可读性。

   <span style="color:green">正例</span>： 

   ```java
   if (isEmpty(user)) {
     // doSomething...
   }
   ```

   <span style="color:red">反例</span>：

   ```java
   if (userList == null || userList.size() == 0) {
     // doSomething...
   }
   ```

   

4. 【推荐】除常用方法（如getXxx/isXxx）等外，不要在条件判断中执行其它复杂的语句，将复杂逻辑判断的结果赋值给一个有意义的布尔变量名，以提高可读性。 
  <br><span style="color:orange">说明</span>：很多if语句内的逻辑相当复杂，阅读者需要分析条件表达式的最终结果，才能明确什么样的条件执行什么样的语句，那么，如果阅读者分析逻辑表达式错误呢？ <br><span style="color:green">正例</span>： 

  ```java
  // 伪代码如下 
  final boolean existed = (file.open(fileName, "w") != null) && (...) || (...); 
  if (existed) {    
     ... 
  }  
  ```
<span style="color:red">反例</span>：
  
  ```java
  if ((file.open(fileName, "w") != null) && (...) || (...)) {     
    ... 
  }
```
  

  
5. 【推荐】避免采用取反逻辑运算符。 
  <br><span style="color:orange">说明</span>：取反逻辑不利于快速理解，并且取反逻辑写法必然存在对应的正向逻辑写法。 
  <br><span style="color:green">正例</span>：使用if (x < 628) 来表达 x 小于628。
  <br><span style="color:red">反例</span>：使用if (!(x >= 628)) 来表达 x 小于628。

### switch...case 语句

1. 在一个switch块内，每个case要么通过break/return等来终止，要么注释说明程序将继续执行到哪一个case为止；在一个switch块内，都必须包含一个default语句并且放在最后，即使空代码。 

2. 大多数时候其实我们并不需要 switch...case 语句，在获取中文名字的场景的时候更好的做法是将数据与逻辑分开，更加易于扩展。

   <span style="color:green">正例</span>：

   ```java
   private final static Map<Integer, String> STATUS_NAME_MAP = new HashMap<>(){{
     put(0, "未支付");
     put(1, "已支付");
     put(2, "已发货");
     put(3, "已签收");
   }};
   
   private final static String NOT_FOUND_STATUS = "未找到";
   
   public String getStatusName(int status) {
     String statusName = NOT_FOUND_STATUS;
     String name = STATUS_NAME_MAP.get(status);
     if (isNotEmpty(name)) {
       statusName = name;
     }
     return statusName;
   }
   
   ```

   <span style="color:red">反例</span>：

   ```java
   public String getStatusName(int status) {
     String statusName = "";
     switch(status) {
       case 0:
         statusName = "未支付";
         break;
       case 1:
         statusName = "已支付";
         break;
       case '2':
         statusName = "已发货";
         break;
       case '3':
         statusName = "已签收";
         break;
       default:
         statusName = "未找到";
     }
     return statusName;
   }
   ```

   

3. 