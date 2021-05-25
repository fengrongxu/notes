# JAVA15

## wrapper_

### WrapperType

```java
package com.study.wrapper;

public class WrapperType {
    public static void main(String[] args) {
        //boolean->Boolean
        //char->Character
        //byte->Byte
        //short->Short
        //int->Integer
        //long-Long
        //float->Float
        //double->Double

    }
}

```

### Integer01

```java
package com.study.wrapper;

public class Integer01 {
    public static void main(String[] args) {
        //演示int->Integer
        //jdk5前是手动装箱和拆箱
        //手动装箱
        int n1=100;
        Integer integer=new Integer(n1);
        Integer integer1=Integer.valueOf(n1);
        //手动拆箱
        //Integer->int
        int i=integer.intValue();
        //jdk5之后 就可以自动装箱和自动拆箱了
        int n2=200;
        //自动装箱->Integer
        Integer integer2=n2;//底层是用的是Integer.valueOf(n2)
        //自动拆箱
        int n3=integer2;//底层使用的是Integer.intValue()
    }
}

```

### Byte

![1621933360845](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\1621933360845.png)

### WrapperExercise01

```java
package com.study.wrapper;

public class WrapperExercise01 {
    public static void main(String[] args) {
        Double d=100d;//ok,自动装箱 Double.valueOf(100d)
        Float f=1.5f;//ok 自动装箱 Float.valueOf(1.5f)
        Object obj1=true?new Integer(1):new Double(2.0);//三元运算符 是一个整体
        System.out.println(obj1);//1.0

    }
}

```

### WrapperExercise02

```java
package com.study.wrapper;

public class WrapperExercise02 {
    public static void main(String[] args) {
        Integer i=new Integer(1);
        Integer j=new Integer(1);
        System.out.println(i==j);//False
        //所以，这里主要是看范围-128~127 就是直接返回
        /*
          public static Integer valueOf(int i) {
        if (i >= IntegerCache.low && i <= IntegerCache.high)
            return IntegerCache.cache[i + (-IntegerCache.low)];
        return new Integer(i);
    }

         */
        Integer m=1;//底层Integer.valueOf(1)
        Integer n=1;//Integer.valueOf(1)
        System.out.println(m==n);//T
        //所以，这里主要是看范围-128~127 就是直接返回
        //否则就new Integer(xx);
        Integer x=128;//底层Integer.valueOf(128)
        Integer y=128;//底层Integer.valueOf(128)
        System.out.println(x==y);//F
    }
}

```

### WrapperExercise03

```java
package com.study.wrapper;

public class WrapperExercise03 {
    public static void main(String[] args) {
        Integer i1 = new Integer(127);
        Integer i2 = new Integer(127);
        System.out.println(i1==i2);//F 不同对象
        Integer i3 = new Integer(127);
        Integer i4 = new Integer(127);
        System.out.println(i3==i4);//F 不同对象
        Integer i5=127; //Integer.valueOf(127);
        Integer i6=127;
        System.out.println(i5==i6);//T -128~127
        Integer i7=128;
        Integer i8=128;
        System.out.println(i7==i8);//F -128~127
        Integer i9=127;
        Integer i10 = new Integer(127);
        System.out.println(i9==i10);//F 不同对象
        Integer i11=127;
        int i12=127;
        System.out.println(i11==i12);//T 有int 比值
        Integer i13=128;
        int i14=128;
        System.out.println(i13==i14);//T 有int 比值

    }
}

```

## string_

### Stirng01

```java
package com.study.string_;

public class String01 {
    public static void main(String[] args) {
        //1.String 对象于保存字符中，也就是一组字符序列
        //2."Jack"字符串常量，双引号括起的字符序列
        //3.一个字符（不分字母还是汉字）占两个字节
        //4.String有很多的构造器
        //5.String 类实现了接口Serializable （String可以串行化，可以在网络上传输）
        //6.String 是final类 不能被继承
        //7.String 有属性 private final char value[];用于存放字符串内容
        //8.value 是final类型 不可以修改 即value不能指向新的地址 但是单个字符内容是可以变化的
        String name="Jack";
        name="tom";
        final char[] value={'a','b','c'};
        char[] v2={'t','o','m'};
        value[0]='H';
        //value=v2; 不可以修改value的地址
    }
}

```

### StringExercise03

```java
package com.study.string_;

public class StringExercise03 {
    public static void main(String[] args) {
        String a="FRX";//a指向 常量池的“FRX”
        String b=new String("FRX");//b指向堆中空间
        System.out.println(a.equals(b));//T
        System.out.println(a==b);//F
        System.out.println(a==b.intern());//intern方法 //T
        System.out.println(b==b.intern());//F
        //当调用intern方法时，如果池已经包含一个等于此 String对象的字符串（用equals（Object）方法确定），
        // 则返回池中的字符串。否则，将此String对象添加到池中，并返回此String对象的引用
        // b.intern()方法最终返回的是   常量池的地址（对象）。
    }
}

```

### StringExercise04

```java
package com.study.string_;

public class StringExercise04 {
    public static void main(String[] args) {
        String s1="frx";//指向常量池 frx
        String s2="java";//指向常量池 java
        String s4="java";//指向常量池 java
        String s3=new String("java");
        System.out.println(s2==s3);//F
        System.out.println(s2==s4);//T
        System.out.println(s2.equals(s3));//T
        System.out.println(s1==s2);//F
    }
}

```

### StringExercise05

```java
package com.study.string_;

public class StringExercise05 {
    public static void main(String[] args) {
        Person p1 = new Person();
        p1.name="frx";
        Person p2 = new Person();
        p2.name="frx";
        System.out.println(p1.name.equals(p2.name));//T
        System.out.println(p1.name==p2.name);//T
        System.out.println(p1.name=="frx");//T
        String s1=new String("zbc");
        String s2 = new String("zbc");
        System.out.println(s1==s2);//F



    }
}
class Person{
    String name;
}
```

### StringExercise06

```java
package com.study.string_;

public class StringExercise06 {
    public static void main(String[] args) {
        String s1="hello"+"abc";//等价String s1="helloabc";
        String s2="helloabc";
        //这里只创建了一个对象
        String a="hello";//创建a对象
        String b="abc";//创建b对象
        String c=a+b;
        //1.先创建StringBuilder sb=new StringBuilder();
        //2.执行 sb.append("hello")
        //3.sb.append("abc")
        //4.String c=sb.ToString()
        //a指向池中hello  b指向池中abc
        //最后其实是c指向堆中的对象 (String)value[]->池中"helloabc"
        //创建了三个对象
        String s3=a+"h";
        //hello已经使用过了 不再创建 所以是两个对象
        System.out.println(a==c);//F  a指向常量池   c指向堆中对象 (String)value[]->池中"helloabc"
        System.out.println(s1==s2);//T
        //常量相加是在池中 变量相加是在堆中
        String s6=(a+b).intern();
        System.out.println(s2==s6);//T
        System.out.println(s2.equals(s6));//T
    }
}

```

### StringExercise10

```java
package com.study.string_;

public class StringExercise10 {
    public static void main(String[] args) {
        Test ex = new Test();
        ex.change(ex.str, ex.ch);
        System.out.print(ex.str+" and ");
        System.out.println(ex.ch);  // hsp and hava

    }
}
class Test{
    String str=new String("hsp");
    final char[] ch={'j','a','v','a'};
    public void change(String str,char ch[]){
        str="java";
        ch[0]='h';
    }
}
```

### 	StringMethod01

```java
package com.study.string_;

public class StringMethod01 {
    public static void main(String[] args) {
        //1.equals方法区分大小写
       String str1="frx";
       String str2="frx";
        System.out.println(str1.equals(str2));
        //2.equalsIgnoreCase 忽略大小写 判断内容是否相等
        String name="john";
        if("john".equalsIgnoreCase(name)){
            System.out.println("Success");
        }
        //3.length 获取字符的个数 字符串的长度
        System.out.println("frx".length());
        //4.indexOf 获取字符串对象中第一次出现的索引，索引从0开始 如果找不到 返回-1
        String s1="wdada@dyhsdsj";
        int index=s1.indexOf('@');
        System.out.println(index);
        //5.lastIndexOf 获取字符 在字符串最后一次出现的索引 索引从零 开始 找不到 返回-1
        String s2="wdada@dyhsdsj";
        int index2=s1.lastIndexOf('@');
        System.out.println(index2);
        //6.substring截取指定范围的字符串
        System.out.println(name.substring(2));//截取后面的字符
    }
}

```

### StringMethod02

```java
package com.study.string_;

import java.util.Locale;

public class StringMethod02 {
    public static void main(String[] args) {
        //1.toUpperCase转成大写
        String s="hello";
        System.out.println(s.toUpperCase());
        //2. toLowerCase
        System.out.println(s.toLowerCase());
        //3.concat拼接字符串
        String s1="frx";
        s1=s1.concat("f").concat("f").concat("f");
        System.out.println(s1);
        //4.replace 替换字符串中的字符
        s1="adc,ddd,dab,gaf";
        s1=s1.replace("ddd","aaa");
        //返回的结果才是 替换过得 对本身的s1没有影响
        System.out.println(s1);
        //5.split分割字符串，对于某些字符串 我们需要转义 比如| \\
        String poem="锄禾日当午，汗滴禾下土，谁知盘中餐，粒粒皆辛苦";
        String split[]=poem.split("，");
         poem="E:\\aa\\bb\\cc";
        split=poem.split("\\\\");
        for (int i = 0; i < split.length ; i++) {
            System.out.println(split[i]);
        }
        //6.toCharArray 转换成字符数组
        s="happy";
        char chs[]=s.toCharArray();
        for (int i = 0; i < chs.length; i++) {
            System.out.println(chs[i]);
        }
        //7.compareTo 比较两个字符串的大小 如果前者大范返回正数
        //后者大 则返回负数  如果相等 返回零
        String s2="frx";
        String s3="frxx";
        System.out.println(s2.compareTo(s3));


    }
}

```

## stringbuffer_

### StringBuffer01

```java
package com.study.stringbuffer_;

public class StringBuffer01 {
    public static void main(String[] args) {
        //1.StringBuffer的直接父类 AbstractStringBuilder
        //2.StringBuffer 实现了Serializable,即StringBuilder的对象可以串行化
        //3.在父类中     AbstractStringBuilder有属性char[] value,不是final
        // 该value数组存放字符串内容，引出存放在堆中
        //4.StringBuffer是final类 不可被继承
        //5.StingBuffer 字符内容存在 char[] value所有的变化(删除，增加)
        //不用每次都创建新的对象 所以它的效率高于String
        StringBuffer stringBuffer = new StringBuffer();
    }
}

```

### StringBuffer02

```java
package com.study.stringbuffer_;

public class StringBuffer02 {
    public static void main(String[] args) {
        //构造器的使用
        //1.创建一个大小为16的char[] 用于存放字符内容
        StringBuffer stringBuffer = new StringBuffer();
        //2.通过构造器指定char[]大小
        StringBuffer stringBuffer1 = new StringBuffer(100);
        //3.通过给一个Sting 创建 StringBuffer char[] 大小就是 str.length()+16
        StringBuffer hello = new StringBuffer("hello");



    }
}

```

### StringBufferExercise01

```java
package com.study.stringbuffer_;

public class StringBufferExercise01 {
    public static void main(String[] args) {
        String str=null;
        StringBuffer sb=new StringBuffer();
        sb.append(str);//底层调用的是AbstractStringBuffer的 appendNull
        System.out.println(sb.length());//4
        System.out.println(sb);//null
        //下面的构造器 会抛出空指针异常
        StringBuffer stringBuffer = new StringBuffer(str);
        //super(str.length()+16);
        System.out.println(stringBuffer);

    }
}

```

### StringBufferExercise02

```java
package com.study.stringbuffer_;

public class StringBufferExercise02 {
    public static void main(String[] args) {
        /*
        输入商品价格 要求打印效果实例，试用前面学习的方法完成：
        商品名 商品价格
        手机 123,45.59


        思路分析
        1.先定义一个Scanner对象，接受用户输入的价格 ·（String)
        2.希望使用到StringBuffer的 insert的    需要将String转成 StringBugger
        3.然后使用相关方法进行字符串的处理
         */
        String input="123456.626";
        StringBuffer stringBuffer=new StringBuffer(input);
        int sb= stringBuffer.lastIndexOf(".");
        stringBuffer=stringBuffer.insert(sb-3,",");
//        for (int i = stringBuffer.lastIndexOf(".")-3; i >0 ; i-=3) {
//            stringBuffer.insert(i,",");
//        }
        System.out.println(stringBuffer);//123,456.626 

    }
}

```

### StringBufferMethod

```java
package com.study.stringbuffer_;

public class StringBufferMethod {
    public static void main(String[] args) {
        //1.append追加 返回的还是StringBuffer
        StringBuffer stringBuffer = new StringBuffer("hello");
        stringBuffer.append("a");
        stringBuffer.append("n");
        stringBuffer.append("c").append("c");
        System.out.println(stringBuffer.toString());
        //2.delete 删除  [1,3)
        //删除>=start&&<end的字符串
        System.out.println(stringBuffer.delete(1, 3));
        //3.replace 替换 [2,4)
        System.out.println(stringBuffer.replace(2,4,"x"));
        //4.indexOf 查找指定的字符串第一次出现的位置 如果找不到 返回-1
        int index=stringBuffer.indexOf("x");
        System.out.println(index);
        //5.insert 插入 原来索引为的位置自动后移
        System.out.println(stringBuffer.insert(5,"obj"));

    }
}

```

## stringbuilder_

### StringBuilder01

```java
package com.study.stringbuilder_;

public class StringBuilder01 {
    public static void main(String[] args) {
        //1.StringBuilder 继承AbstractStringBuilder 类
        //2.实现了Serializable,说明StringBuilder对象可以串行化（对象可以网络传输，可以保存到文件）
        //3.StringBuilder 是final类 不能被继承
        //4.StringBuilder 对象字符序列仍然是存放 在其父类 AbstractStringBuilder的 char[] value
        //  因此字符序列是在堆中
        //5.StringBuilder的方法 没有做互斥处理
        StringBuilder stringBuilder = new StringBuilder();

    }
}

```

### StringBuilderVSStringBufferVSString

```java
package com.study.stringbuilder_;

public class StringBuilderVSStringBufferVSString {
    public static void main(String[] args) {
        String test="";
        long startTime=0L;
        long endTime=0L;
        StringBuffer buffer = new StringBuffer("");
        StringBuilder builder = new StringBuilder("");
        startTime=System.currentTimeMillis();
        for (int i = 0; i < 20000; i++) {
            buffer.append(String.valueOf(i));
        }
        endTime=System.currentTimeMillis();
        System.out.println("StringBuffer的执行时间："+(endTime-startTime));
        startTime=System.currentTimeMillis();
        for (int i = 0; i < 20000; i++) {
            builder.append(String.valueOf(i));

        }
        endTime=System.currentTimeMillis();
        System.out.println("StringBuilder的执行时间："+(endTime-startTime));
        startTime=System.currentTimeMillis();
        for (int i = 0; i < 20000; i++) {
           test=test+i;

        }
        endTime=System.currentTimeMillis();
        System.out.println("String的执行时间："+(endTime-startTime));
    }
    }
/*
使用的原则，结论：
1.如果字符存在大量的修改操作，一般使用StringBuffer或StringBuilder
2.如果字符存在大量的修改操作，并在单线程的情况下，使用StringBuilder
3.如果字符存在大量的修改操作，并在多线程的情况下，使用StringBuffer
4.如果我们字符串很少修改，被多个对象引用，使用String，比如配置信息等
 */


```

