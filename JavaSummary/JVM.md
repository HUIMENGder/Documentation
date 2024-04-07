# jvm总体梳理 
## 类的加载机制
### 什么是来的加载机制  
类的加载是指将类的.class的文件的二进制数据读取到内存中将其放在数据区的方法中，然后在堆区创建一个java.lang.Class对象，用来封装类在方法去的数据结构。类的加载最终的产物是在堆区产生的一个Class的对象，Class封装了类在方法区的数据结构，并且向Java程序员提供访问方法内数据结构的接口。  
### 类的声明周期  
类的声明周期包括几部分：加载，连接，初始化，使用和卸载，其中前三步是类的加载过程。  
* 加载：查找并加载类的二进制数据，在堆中也创建一个Java.lang.Class的对象 
* 连接：连接又包括三部分：验证，准备，