Init read me


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
