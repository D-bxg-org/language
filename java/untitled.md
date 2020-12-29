# 编译java总结

## Java:java-&gt;class-&gt;jar

我们在没使用maven管理项目前， 编译一个以.java结尾的文件，经历以下几个步骤：

1. 用javac，把在src（源代码）文件夹下的.java文件编译到bin目录下，变成.class文件
2. 在用java，执行bin中含有main方法的.class文件，一个java项目就跑起来了。

我们注意到，我们jdk版本的区别，实际上只影响编译成的class是何种样子的，而jre决定的是class变成何种可跑在jvm上的二进制机器码。

java中的jdk是向下兼容的，也就是说，低版本的jdk编译出来的.class文件，可以跑在高版本jdk中自带的jre中的jvm上，是因为高版本自带的jre兼容低版本jdk编译出来的.class文件。

## 怎么在idea中打jar包？

我们常说的build就是在打jar包，跳过了bin这一步，在idea中，会被放在target中。

使用Junit又是另外一种情况

参考[如何把我的Java程序变成exe文件？](https://blog.csdn.net/weixin_43149083/article/details/89639747)

## jar作用

我们可以使用jar，把bin中的.class文件集体打成一个jar包，然后在其他地方用java执行起来。

## 怎么变成.exe文件

而在windowsOS上，我们一般的可执行文件后缀是.exe，那就需要进一步把jar包变成exe文件

参考：[【知乎】如何把我的Java程序变成exe文件？](https://zhuanlan.zhihu.com/p/77354191)

## war包是什么

如果我们的项目是一个web项目，那么就可以打成war包，运行只需要放在有tomcat的项目中的web-inf文件夹下（此处不明确，我还没学到，但原理大抵如此），用tomcat执行起来，war包就会被tomcat自动解析，执行。

参考：[Java项目部署发布与访问【面试+提高】](https://www.jianshu.com/p/cfc554a97396)

## 各种环境

我们知道，我们写java时的环境叫开发环境，而其他的是何种意思？

参考：[开发环境、测试环境、生产环境 到底是什么？](https://blog.csdn.net/qq_36538012/article/details/78552074)

## Maven - 打包可执行jar包

[用命令的方式，把maven打包jar包](https://www.jianshu.com/p/0d85d0539b1a)

[【Maven学习】Maven打包生成普通jar包、可运行jar包、包含所有依赖的jar包](https://blog.csdn.net/u013177446/article/details/54134394)

### maven中的方法

其实，不能叫做maven中的方法。

我在研究多个版本的jdk怎么切换时，看到了一种方法，使用批处理文件，也就是windows上的.bat文件。

在讲和批处理文件有什么关系前，我想先讲下dos，也就是我们win键+R键唤出的运行中，输入cmd出来的管理员窗口。

它首先有路径，在路径后我们输入的指令就是我们在某个路径下，双击某个文件的作用。

而有些文件，它包含一些参数，例如：java -jar。这里的-jar就是java的属性、或者讲方法。

那么我现在（2020年12月6日16:33:13）理解的，maven包含多个生命周期，实际上就是后面的方法调用前一个方法，我们执行哪个方法，就是执行该方法和之前的所有方法。

至于maven是怎么打包、怎么执行、目前还不得而知。（还没学到）

