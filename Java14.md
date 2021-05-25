# JAVA14

## enum_

### Enumeration01

```java
package com.study.study13enum_;

public class Enumeration01 {
    public static void main(String[] args) {
        //使用
        Season spring = new Season("春天", "温暖");
        Season summer = new Season("夏天","炎热");
        Season autumn = new Season("秋天","凉爽");
        Season winter = new Season("冬天","寒冷");
        //因为对于季节而言，她的对象是具体的 固定的 不会有更多
        //不能体现季节是固定的  引出枚举类


    }
}
class Season{
    private String name;
    private String desc;//描述

    public Season(String name, String desc) {
        this.name = name;
        this.desc = desc;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getDesc() {
        return desc;
    }

    public void setDesc(String desc) {
        this.desc = desc;
    }
}
```

### Enumeration02

```java
package com.study.study13enum_;

public class Enumeration02 {
    public static void main(String[] args) {
        System.out.println(Season1.AUTUMN);
        System.out.println(Season1.SPRING);
    }


}
//演示定义枚举实现
class Season1 {
    private String name;
    private String desc;//描述
    //1.将构造器私有化 目的 防止直接new
    //2.去掉set方法 防止属性被修改
    //3.在Season内部，直接创建固定的属性
    //4.可以加入final 修饰符
    public static final Season1 SPRING =new Season1("春天", "温暖");
    public static final Season1 SUMMER =new Season1("夏天", "炎热");
    public static final Season1 AUTUMN =new Season1("秋天", "凉爽");
    public static final Season1 WINTER =new Season1("冬天", "寒冷");

    private Season1(String name, String desc) {
        this.name = name;
        this.desc = desc;
    }

    @Override
    public String toString() {
        return "Season1{" +
                "name='" + name + '\'' +
                ", desc='" + desc + '\'' +
                '}';
    }

    public String getName() {
        return name;
    }



    public String getDesc() {
        return desc;
    }

}
```

### Enumeration03

```java
package com.study.study13enum_;

public class Enumeration03 {
    public static void main(String[] args) {
        System.out.println(Season2.SPRING);
        System.out.println(Season2.AUTUMN);
        System.out.println(Season2.SUMMER);
        System.out.println(Season2.WINTER);
    }
}
enum Season2{
    //1.使用枚举类 用enum来代替 class
    //2.SPRING("春天", "温暖");  常量名（实参列表）
    //3.如果有多个常量（对象），是用逗号间隔 即可
    //4.如果使用enum来实现枚举，要求将定义对象，写在前面
    //5.如果使用无参构造器，创建常量对象，则可以省略()
    WINTER("冬天", "寒冷"),
    SUMMER("夏天", "炎热"),
    SPRING("春天", "温暖"),
    WHAT,
    AUTUMN("秋天", "凉爽");
    private String name;
    private String desc;//描述
    //


    private Season2() {
    }

    private Season2(String name, String desc) {
        this.name = name;
        this.desc = desc;
    }

    @Override
    public String toString() {
        return "Season1{" +
                "name='" + name + '\'' +
                ", desc='" + desc + '\'' +
                '}';
    }

    public String getName() {
        return name;
    }



    public String getDesc() {
        return desc;
    }

}
```

### EnumExercise01

```java
package com.study.study13enum_;

public class EnumExercise01 {
    public static void main(String[] args) {
        Gender2 boy=Gender2.BOY;
        Gender2 boy1=Gender2.BOY;
        System.out.println(boy);
        System.out.println(boy==boy1);

    }
}
enum Gender2{
    BOY,GIRL;

//    @Override
//    public String toString() {
//        return name;
//    }
}

```

### EnumExercise02

```java
package com.study.study13enum_;

public class EnumExercise02 {
    public static void main(String[] args) {
        Week weeks[]=Week.values();
        for(Week week:weeks){
            System.out.println(week);

        }


    }
}
enum Week{
    Monday("星期一"),
    Tuesday("星期二"),
    WEDNESDAY("星期三"),
    THURSDAY("星期四"),
    FRIDAY("星期五"),
    SATURDAY("星期六"),
    SUNDAY("星期天");


    private String name;

    private Week(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return name;
    }
}
```

### EnumMethod

```java
package com.study.study13enum_;

import com.study.study13enum_.Season2;

public class EnumMethod {
    public static void main(String[] args) {
        //使用Season2枚举类，来演示各种方法
        Season2 autumn=Season2.AUTUMN;
        //输出枚举对象的名字
        System.out.println(autumn.name());
        //ordinal()输出对象的编号 从零开始
        //AUTUMN 枚举对象是第五个 所以输出4
        System.out.println(autumn.ordinal());
        //从反编译可以看出 values方法，返回Season2[]
        //含有定义的所有枚举对象
        Season2 values[]=Season2.values();
        System.out.println("=======遍历取出枚举对象=======");
        for(Season2 season:values){//增强for循环
            System.out.println(season);
        }
        //valueOf:将字符串转化成枚举对象，要求字符串必须为已有的常量名，否则报异常
        //执行流程
        //1.根据你输入的：“AUTUMN”到Season2的枚举对象去查找
        //2.如果找到了，就返回，如果没有 就报错
        Season2 autumn1=Season2.valueOf("AUTUMN");
        System.out.println("autumn1="+autumn1);
        System.out.println(autumn==autumn1);
        //compareTo:比较两个枚举常量，比较的是编写
        //1.就是把Season.AUTUMN 枚举对象的编号和Season.SUMMER 枚举对象的编号进行比较
        System.out.println(Season2.AUTUMN.compareTo(Season2.SUMMER));

//
//        int nums[]={1,2,9};
//        //普通for循环
//        System.out.println("=======普通for循环==========");
//        for (int i = 0; i < nums.length; i++) {
//            System.out.println(nums[i]);
//        }
//        System.out.println("========增强for循环==========");
//        for(int i:nums){//执行流程 依次从nums数组中 取出数据 取出完毕 退出增强for循环
//            System.out.println("i="+i);
//
//        }
    }
}

```

## exception_

### try_

#### Exception01

```java
package com.study.study15exception_;

public class Exception01 {
    public static void main(String[] args) {

        int num1=10;
        int num2=0;
        //1.当执行到num1/num2 时 程序就会抛出异常 ArithmeticException 算术异常
        //2.当抛出异常后，程序就退出，崩溃了，下面的代码就不再执行
        //3.这样的程序不好 不应该出现一个不算致命的问题 就导致整个系统崩溃
//        int res=num1/num2;
        //4.如果程序员觉得一带代码会出现异常 可以使用try-catch异常处理机制来解决
        //从而保证代码的健壮性
        //6.如果进项异常处理，那么即使出现了异常，程序可以继续执行
        try{//5.选中带代码块 ctrl alt t 选中 try-catch
            int res=num1/num2;
        }catch (Exception e){
//            e.printStackTrace();
            System.out.println(e.getMessage());//输出异常信息
        }



            System.out.println("程序继续执行...");

    }
}

```

#### Exception02

```java
package com.study.study15exception_;

public class Exception02 {
    public static void main(String[] args) {
//        Throwable
    }
}

```

#### Throwable

![1621932952986](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\1621932952986.png)

### throw_

#### Throws01

```java
package com.study.study15exception_.throws_;

import java.io.FileInputStream;

public class Throws01 {
    public static void main(String[] args) {

    }
    public void f2() throws Exception {
        //创建一个文件流对象
        //1.这里的异常是一个FileNotFoundException 编译异常
        //2.使用前面讲过的 try-catch_finally
        //3.使用throws，抛出异常，让调用f2方法的调用者（方法）处理
        //4.throws后面的异常可以是方法中产生的异常，也可以是它的父类
        //5.throws关键字后也可以是 异常列表，既可以抛出多个异常

        FileInputStream fis = new FileInputStream("d://aa.xt");

    }
}

```

#### ThrowsDetail

```java
package com.study.study15exception_.throws_;

import java.io.FileNotFoundException;

public class ThrowsDetail {
    public static void main(String[] args) {
        f2();

    }

    public static void f2() /*throws ArithmeticException*/ {
        //1.对于编译异常，程序中必须处理，比如 try-catch或者 throws
        //2.对于运行时异常，程序中如果没有处理，默认就是throws的方式处理
        int n1 = 0;
        int n2 = 0;
        double res = n1 / n2;
    }

    public static void f1() {
        //1.f()方法 抛出编译异常
        //2.记者时，就要去f1() 必须处理这个编译异常
        //3. （1） throws FileNotFoundException (2) t c f

        try {
            f3();//抛出异常
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }

    }

    public static void f3() throws FileNotFoundException {

    }
    public static void f4(){
        //1.在f4()方法中 调用f5()方法是OK的
        //2.原因是f5()抛出的是运行异常
        //3.而Java 并不要求 程序员显示处理，因为有默认处理机制
        f5();

    }
    public static void f5() throws ArithmeticException{

    }
}
class Father{
    public void method() throws RuntimeException{

    }

}
class Son extends Father{
    //3.子类重写父类的方法时，对抛出异常的规定：子类重写的方法
    // 所抛出的异常要么和父类抛出的异常一致，要么为父类抛出异常的子类型
    @Override
    public void method() throws NullPointerException {
        super.method();
    }
}
```

### CustomException

```java
package com.study.study15exception_.customException_;

public class CustomException {
    public static void main(String[] args) {
        int age=180;
        if(!(age>=8&&age<=120)){
            throw new AgeException("年龄须在18-120之间");

        }
        System.out.println("你的年龄范围是正确的");

    }
}
//自定义的一个异常
//1.一般情况下，我们自定义异常是继承 RuntimeException
//2.即把自定义异常继承运行时异常 好处 我们可以使用默认处理机制
class AgeException extends RuntimeException{
    public AgeException(String message) {
        super(message);
    }
}
```

### ThrowException

```java
package com.study.study15exception_.customException_;

public class ThrowException {
    public static void main(String[] args) {
        try {
            ReturnExceptionDemo.methodA();
        } catch (Exception e) {
            System.out.println(e.getMessage());
            ReturnExceptionDemo.methodB();
        }

    }
}
class ReturnExceptionDemo{
    static void methodA(){
        try {
            System.out.println("进入方法A");
            throw new RuntimeException("制造异常");
        } finally {
            System.out.println("调用A方法的finally");
        }
    }
    static void methodB(){
        try {
            System.out.println("进入方法B");
            return;
        } finally {
            System.out.println("调用B方法的finally");

        }
    }
}
```

