# JUnit-基本用法 #
现在我们将应用简单的例子来一步一步教你如何使用 Junit。  
## 创建一个类 ##
- 在  **C:\ > JUNIT_WORKSPACE** 路径下创建一个名为 MessageUtil.java 的类用来测试。  
```
/*
* This class prints the given message on console.
*/
public class MessageUtil {

   private String message;

   //Constructor
   //@param message to be printed
   public MessageUtil(String message){
      this.message = message;
   }
      
   // prints the message
   public String printMessage(){
      System.out.println(message);
      return message;
   }   
}  
```  
## 创建 Test Case 类 ##
- 创建一个名为 TestJunit.java 的测试类。
- 向测试类中添加名为  testPrintMessage() 的方法
- 向方法中添加 Annotaion @Test
- 执行测试条件并且应用 Junit 的 assertEquals API 来检查  
在 **C:\ > JUNIT_WORKSPACE** 路径下创建一个文件名为 TestJunit.java 的类  
```
import org.junit.Test;
import static org.junit.Assert.assertEquals;
public class TestJunit {
	
   String message = "Hello World";	
   MessageUtil messageUtil = new MessageUtil(message);

   @Test
   public void testPrintMessage() {
      assertEquals(message,messageUtil.printMessage());
   }
}
```  
## 创建 Test Runner 类 ##
- 创建一个 TestRunner 类
- 运用 JUnit 的 JUnitCore 类的 runClasses 方法来运行上述测试类的测试案例  
- 获取在 Result Object 中运行的测试案例的结果
- 获取 Result Object 的 getFailures() 方法中的失败结果
- 获取 Result object 的 wasSuccessful() 方法中的成功结果  
在 **C:\ > JUNIT_WORKSPACE** 路径下创建一个文件名为  TestRunner.java 的类来执行测试案例  
```
import org.junit.runner.JUnitCore;
import org.junit.runner.Result;
import org.junit.runner.notification.Failure;

public class TestRunner {
   public static void main(String[] args) {
      Result result = JUnitCore.runClasses(TestJunit.class);
      for (Failure failure : result.getFailures()) {
         System.out.println(failure.toString());
      }
      System.out.println(result.wasSuccessful());
   }
}  	
```   
用 javac 编译 MessageUtil、Test case 和 Test Runner 类。
```
C:\JUNIT_WORKSPACE>javac MessageUtil.java TestJunit.java TestRunner.java
```  
现在运行 Test Runner 它可以运行在 Test Case 类中定义并提供的测试案例。  
```
C:\JUNIT_WORKSPACE>java TestRunner
```  
检查运行结果  
```
Hello World
true
```  
现在更新 **C:\ > JUNIT_WORKSPACE** 路径下的 TestJunit 来检测失败。改变消息字符串。  
```
import org.junit.Test;
import static org.junit.Assert.assertEquals;
public class TestJunit {
	
   String message = "Hello World";	
   MessageUtil messageUtil = new MessageUtil(message);

   @Test
   public void testPrintMessage() {
      message = "New Word";
      assertEquals(message,messageUtil.printMessage());
   }
}
```  
让我们保持其他类不变，再次尝试运行相同的 Test Runner  
```
import org.junit.runner.JUnitCore;
import org.junit.runner.Result;
import org.junit.runner.notification.Failure;

public class TestRunner {
   public static void main(String[] args) {
      Result result = JUnitCore.runClasses(TestJunit.class);
      for (Failure failure : result.getFailures()) {
         System.out.println(failure.toString());
      }
      System.out.println(result.wasSuccessful());
   }
}
```  
现在运行在 Test Case 类中提供的即将运行测试案例的 Test Runner  
```
C:\JUNIT_WORKSPACE>java TestRunner
```  
检查运行结果  
```
Hello World
testPrintMessage(TestJunit): expected:<[New Wor]d> but was:<[Hello Worl]d>
false
```  
