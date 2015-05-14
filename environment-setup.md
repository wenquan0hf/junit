# Junit - 环境设置

## 在线选择 Try it

你真的不需要建立自己的环境去开始学习Java和JUnit 编程语言。原因很简单，我们已经建立了网上的Java 编程环境，所以你可以在做你理论工作的同时编辑和执行网上所有可用的例子。这个可以对你所阅读的东西给你自信以及利用不同的选择检查结果。轻松地修饰任何的例子并直接在网上修改。

尝试下面的例子，在下面的样代码表格中的右上角使用可用选择 **Try It**。

```
public class MyFirstJavaProgram {

    public static void main(String []args) {
       System.out.println("Hello World");
    }
} 
```

对于本教程中所给的大部分例子，你将会找到 **Try it** 选项，所以尽情利用它享受你的学习之旅吧。

## 本地环境建立

JUnit 是 Java 的一个框架，所以最根本的需要是在你的机器里装有 JDK。

## 系统要求

|JDK| 1.5或1.5以上|
|---|:------------|
|内存|没有最小要求|
|磁盘空间|没有最小要求|
|操作系统|没有最小要求|

## 步骤1 - 在你的机器里验证 Java 装置


现在打开控制台，执行以下 **java** 要求。

|OS|任务|命令|
|--:|:---:|:-----|
|Windows|打开命令操作台|c:\> java -version|
|Linux	|打开命令终端|$ java -version|
|Mac	  |打开终端|machine:~ joseph$ java -version|

我们来验证一下所有操作系统的输出：

|OS|输出|
|--:|:---|
|Windows|java 版本 “1.6.0_21” </br> Java（TM）SE 运行环境（build 1.6.0_21-b07）</br>Java 热点（TM）客户端虚拟机（build 17.0-b17，混合模式，共享）|
|Linux	|java 版本“1.6.0_21” </br> Java（TM）SE 运行环境（build 1.6.0_21-b07）</br>Java 热点（TM）客户端虚拟机（build 17.0-b17，混合模式，共享）|
|Mac	  |java 版本“1.6.0_21”</br> Java（TM）SE 运行环境（build 1.6.0_21-b07）</br>Java 热点（TM）64-字节服务器虚拟机（build 17.0-b17，混合模式，共享）|

如果你还没有安装 Java，从以下网址安装 **http://www.oracle.com/technetwork/java/javase/downloads/index.html** Java SDK。我们采用 Java 1.6.0_21 作为本教程的安装版本。


## 步骤2：设置 JAVA 环境


设置 **JAVA_HOME** 环境变量，使之指向基本目录位置，即在你机器上安装 Java 的位置。

|OS|输出|
|:--|:----|
|Windows|设置环境变量 JAVA_HOME to C:\Program Files\Java\jdk1.6.0_21|
|Linux	|输出 JAVA_HOME=/usr/local/java-current|
|Mac	  |输出 JAVA_HOME=/Library/Java/Home|

系统路径添加 Java 编译器位置。

|OS|输出|
|:--|:---|
|Windows|在系统变量路径末端添加字符串 ;C:\Program Files\Java\jdk1.6.0_21\bin|
|Linux|输出 PATH=$PATH:$JAVA_HOME/bin/|
|Mac  |不需要|

使用以上解释的 **Java-version** 命令验证 Java 安装。 

## 步骤3：下载 Junit 档案
从 **http://www.junit.org** 下载 JUnit 最新版本的压缩文件。在编写这个教程的同时，我已经下载了 *Junit-4.10.jar* 并且经他复制到 C:\>JUnit 文件夹里了。

|OS|档案名称|
|:---|:-----|
|Windows|junit4.10.jar|
|Linux	|junit4.10.jar|
|Mac	  |junit4.10.jar|

## 步骤4：设置 JUnit 环境

设置 **JAVA_HOME** 变量，使之指向基本目录位置，即在你机器上安装 JUNIT 压缩文件的位置。假设，我们已经在以下不同的操作系统的 JUNIT 文件夹里存储了 junit4.10.jar。

|OS|输出|
|:--|:----|
|Windows|设置环境变量 JUNIT_HOME 到 C:\JUNIT|
|Linux	|输出 JUNIT_HOME=/usr/local/JUNIT|
|Mac    |输出 JUNIT_HOME=/Library/JUNIT|

## 步骤5：设置类路径变量

设置 **CLASSPATH** 环境变量，使之指向 JUNIT 压缩文件位置。假设，我们已经在以下不同的操作系统的 JUNIT 文件夹里存储了 junit4.10.jar 。

|OS|输出|
|:--|:---|
|Windows|设置环境变量 CLASSPATH 到 %CLASSPATH%;%JUNIT_HOME%\junit4.10.jar;.;|
|Linux	|输出 CLASSPATH=$CLASSPATH:$JUNIT_HOME/junit4.10.jar:.|
|Mac	  |输出 CLASSPATH=$CLASSPATH:$JUNIT_HOME/junit4.10.jar:.|

## 步骤6：测试 JUnit 建立

在 **C:\ > JUNIT_WORKSPACE** 中创建一个 java 类文件，名称为 TestJunit。

```
  
import org.junit.Test;
import static org.junit.Assert.assertEquals;
public class TestJunit {
   @Test
   public void testAdd() {
      String str= "Junit is working fine";
      assertEquals("Junit is working fine",str);
   }
}
```

在 **C:\ > JUNIT_WORKSPACE** 中创建一个 java 类文件，名称为TestRunner，来执行测试用例。

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

## 步骤7：验证结果

利用 **javac** 编译器按照以下方式编写类。

```
C:\JUNIT_WORKSPACE>javac TestJunit.java TestRunner.java
```

现在运行 Test Runner 来看结果。

```
C:\JUNIT_WORKSPACE>java TestRunner
```

验证输出。

```
ture
```


