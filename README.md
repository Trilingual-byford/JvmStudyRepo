Best video tutorial(Chinese):https://www.bilibili.com/video/BV1yE411Z7AP?p=12

Java Code,file name:StackStruTest.java
````
public class StackStruTest {
    public static void main(String[] args) {
        int i=2;
        int j=3;
        int k=i+3;
    }
}

javac StackStruTest.java
````

````

❯ ls
StackStruTest.class StackStruTest.java
 javap -v StackStruTest.class
❯ javap -v StackStruTest.class
Classfile /Users/byford/IdeaProjects/JVMDemo/src/StackStruTest.class
  Last modified Jan 11, 2021; size 291 bytes
  SHA-256 checksum 4739113452c81074a9a909c33ed7ebdd2d5db8529e439b8002b70a2ce0db2917
  Compiled from "StackStruTest.java"
public class StackStruTest
  minor version: 0
  major version: 57
  flags: (0x0021) ACC_PUBLIC, ACC_SUPER
  this_class: #7                          // StackStruTest
  super_class: #2                         // java/lang/Object
  interfaces: 0, fields: 0, methods: 2, attributes: 1
Constant pool:
   #1 = Methodref          #2.#3          // java/lang/Object."<init>":()V
   #2 = Class              #4             // java/lang/Object
   #3 = NameAndType        #5:#6          // "<init>":()V
   #4 = Utf8               java/lang/Object
   #5 = Utf8               <init>
   #6 = Utf8               ()V
   #7 = Class              #8             // StackStruTest
   #8 = Utf8               StackStruTest
   #9 = Utf8               Code
  #10 = Utf8               LineNumberTable
  #11 = Utf8               main
  #12 = Utf8               ([Ljava/lang/String;)V
  #13 = Utf8               SourceFile
  #14 = Utf8               StackStruTest.java
{
  public StackStruTest();
    descriptor: ()V
    flags: (0x0001) ACC_PUBLIC
    Code:
      stack=1, locals=1, args_size=1
         0: aload_0
         1: invokespecial #1                  // Method java/lang/Object."<init>":()V
         4: return
      LineNumberTable:
        line 1: 0

  public static void main(java.lang.String[]);
    descriptor: ([Ljava/lang/String;)V
    flags: (0x0009) ACC_PUBLIC, ACC_STATIC
    Code:
      stack=2, locals=4, args_size=1
         0: iconst_2
         1: istore_1
         2: iconst_3
         3: istore_2
         4: iload_1
         5: iconst_3
         6: iadd
         7: istore_3
         8: return
      LineNumberTable:
        line 3: 0
        line 4: 2
        line 5: 4
        line 6: 8
}
SourceFile: "StackStruTest.java"
````
### JVM：商用
 - JRockit 专注于服务端，特别适用于延迟敏感性应用。
 - IBM J9
 - hotSpot 编译执行和解释执行中取得平衡
### ClassLoading:Verify(文件格式验证，元数据验证，字节码验证，符号引用验证etc..)->prepare->Resolve

### 虚拟机自带的加载器
 - BootStrap classLoader 使用C/C++编写 程序启动时 无法获取对象  用来加载Java的核心库 String int etc..
 - Extension ClassLoader 扩展类加载器
 - App ClassLoader 加载用户编写的类的加载器
 

      stack=2, locals=4, args_size=1C/
      stack=2, locals=4, args_size=1
      
- Had a rest on Janurary 16
- parents delegation model
- PC register 线程私有（Processor register） 无内存溢出
- 垃圾回收不涉及栈内存  因为Stack frame里面存储的数据 会随着里面的方法调用完而被回收，一般指的垃圾回收、优化等等 是针对堆内的数据而言 
- jps 查看当前系统有哪些java进程 
- jconsole 图形界面的，多功能的检测工具，可以连续检测检测
- jvisualvm内存诊断工具
- Java二进制字节码（包含类的基本信息，常量池，类方法定义包含了虚拟机指令）
- Java instruction code   ldc=load constant : it loads an item from constant pool onto the stack
- StringTable垃圾回收 性能调优 String.intern();
- Direct Memory 不收JVM内存回收管理 分配回收成本高 但是读写性能高 常用于NIO操作用于数据缓冲区
- Direct buffer:https://www.fusion-reactor.com/blog/evangelism/understanding-java-buffer-pool-memory-space/ 
- -XX:+DisableExplicitGc 禁用显式的垃圾回收 System.gc();
- 垃圾回收方法：引用计数法（弊端无法解析循环引用） 可达性分析算法 GCROOT  强引用 -> 软引用 -> 弱引用 -> 虚引用
- 垃圾回收算法 ：标记清除算法（内存碎片问题） 标记整理（引用地址改变） 复制算法（From To 算法）
- --XX:+UseSerialGC 串行（单线程垃圾回收 回收时阻塞其他线程）
- --XX:+UseParallelGc 多线程垃圾回收 吞吐量优先 ParallelGcThreads=n 设置垃圾回收线程数
- -XX:+UseConcMarkSweepGc --parallelGcThreads=n 
- 确定目标
- 低延迟（增加相应时间）  VS 高吞吐量（做各种科学计算）
- 低延迟G1，CMS，ZGC（ZGC）
- 高吞吐量 ParallelGC
-  5.3 最快的GC是不发生GC
-  1，数据是不是太多？ result=statement.executeQuery("Select * from table limit n")
-  2，数据表示是不是太臃肿  多取了无用的数据/对象大小太大 Integer 24->int 4
-  3,内存泄漏  软弱引用  使用第三方的缓存实现 Redisなど
