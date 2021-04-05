# Java08

## 1.pkg

### import01

```java
package com.study1.pkg;

import java.util.Arrays;

//注意：我们需要使用哪个类 就导入哪个类即可
//import java.util.Scanner;//表示只会引入java.util的Scanner
//import java.util.*;//表示将java.util 包下的所有类都引入（导入）
public class Import01 {
    public static void main(String[] args) {
    //使用系统提供 Arrays 完成 数组排序
        int arr[]={-1,20,2,13,3};
        //比如对其进行排序
        //传统方法是，自己编写排序（冒泡）
        //系统是提供相关的类 可以方便完成 Arrays
        Arrays.sort(arr);
        //输出排序结果
       for(int i=0;i<arr.length;i++){
           System.out.print(arr[i]+"\t");
       }
       }
}

```

### PkgDetails

```java
//package的作用是声明当前类所在的包，需要放在类的（或者文件）的最上面，
//一个类中最多有只有一句 package
package com.study1.pkg;
import java.util.Scanner;

//import 指令 位置放在package的下面，在类定义前面，可以有多局且没有顺序
public class PkgDetail {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
    }
}

```

### Test

```java
package com.study1.pkg;

import com.study1.modifier.A;

public class Test {
    public static void main(String[] args) {
        A a = new A();
        //在不同的包下，可以访问public修饰访问的属性或方法，
        // protected，默认，private修饰访问的属性或方法
        System.out.println(a.n1);//100
        a.m1();
        //不同包不能使用a.m2 a.m3 a.m4

    }

}

```

## modifier

### A

```java
package com.study1.modifier;

public class A {
    //四个属性,分别用不同的修饰符
    public int n1=100;
    protected int n2=200;
    int n3=300;
    private int n4=400;
    public void m1(){
        //在同一个类中，可以访问public protected 默认 private修饰访问的属性或方法
        System.out.println("n1="+n1+" n2="+n2+" n3="+n3+" n4="+n4);
    }
    protected void m2() {
    }
        void m3(){

        }

    private void m4(){

    }
    public void hi(){
       // 在同一类中，可以访问 private protected 默认 public
        m1();
        m2();
        m3();
        m4();


    }
}






//访问级别 | 访问修饰符 | 同类 | 同包 | 子类 | 不同包
//公开    |  public   | √   |  √  |  √   |  √
//受保护   | protected | √   |  √  |  √   |  √
//默认    | 没有修饰符   | √  |   √ |   ×  |  ×
//私有    |  private   | √   |  ×  |   ×  |  ×
//使用注意事项
//1.修饰符可以用来修饰类中的属性，成员方法以及类
//2.只有默认的和public才能修饰类，并且遵循上述访问权限的特点
//3.成员方法的访问规则和属性完全一样
```



## B

```java
package com.study1.modifier;

public class B {
    public void say(){
        A a = new A();
        //在同一个包下，可以访问 public protected 和默认修饰的属性或方法，不能访问private
        System.out.println("n1="+a.n1+" n2="+a.n2+" n3="+a.n3);
        a.m1();
        a.m2();
        a.m3();
        //

    }
}

```

## Test

```java
package com.study1.modifier;

public class Test {
    public static void main(String[] args) {
        A a = new A();
        a.m1();
        B b = new B();
        b.say();


    }
}
//只有默认和public可以修饰类




```



