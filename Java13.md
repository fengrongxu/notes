# JAVA13

## static_

### ChildGame

```java
package com.study7static_;

public class ChildGame {
    public static void main(String[] args) {

        Child child1 = new Child("白骨精");
        child1.join();

        Child child2 = new Child("老鼠精");
        child2.join();

        Child child3 = new Child("狐狸精");
        child3.join();
        child3.count++;
        System.out.println("共有"+child1.count+"加入了游戏");


    }
}
class Child {
    private String name;
    public static int count=0;

    public Child(String name) {
        this.name = name;
    }
    public void join(){
        System.out.println(name+"加入了游戏..");
    }


}
```

### Main01

```java
package com.study7static_;

public class Main01 {
    //静态的变量/属性

    private static String name="frx";
    private int n1=100;
    private static void hi(){
        System.out.println("Main01中的hi方法");

    }
    //非静态方法
    public void cry(){
        System.out.println("Main01中的cry方法");
    }

    public static void main(String[] args) {
        //1.静态方法main可以访问本类的静态成员
        System.out.println("name="+name);
        hi();
        //2.静态方法main不可以访问本类的非静态成员
        //cay();
        //3.静态方法main 可以先创建对象在访问非静态方法
        Main01 main01 = new Main01();
        main01.cry();
    }
}

```

### StaticDetail

```java
package com.study7static_;

public class StaticDetail {
    public static void main(String[] args) {
        //静态变量是类加载的时候，就创建了，所以我们没有创建对象实例
        //也可以通过类名.类变量名来访问
        System.out.println(C.address);

    }
}
class B{
    public static int n1=100;
}
class C{
    public static String address="北京";

        }


```

### StaicMethod

```java
package com.study7static_;

public class StaticMethod {
    public static void main(String[] args) {
        Stu Tom = new Stu("Tom");
        Tom.payFee(100);
        Stu jack = new Stu("Jack");
        jack.payFee(200);
        Stu.showFee();

    }
}

class Stu {
    private String name;//普通成员
    //定义一个静态变量，来积累学生的学费
    private static double fee = 0;

    public Stu(String name) {
        this.name = name;
    }

    //1.当方法使用率static修饰后，该方法就是静态方法
    //2.静态方法就可以访问静态属性/变量
    public static void payFee(double fee) {
        Stu.fee += fee;//累计到
    }

    public static void showFee() {
        System.out.println("总学费有：" + Stu.fee);
    }

}

```

### StaticMethodDetail

```java
package com.study7static_;

public class StaticMethodDetail {
    public static void main(String[] args) {
           D.hi();//ok
        //非静态方法，不能通过类名调用
        new D().say();
    }
}
class D{
    private int n1=200;
    private static int n2=100;
    public void say(){

    }
    public static void hi(){
        //类方法中，不允许使用和对象有关的关键字
        //比如this和super.
    }
    //静态方法中，只能访问 静态变量或静态方法
    public static void hello(){
        System.out.println(n2);
        hi();
        //say();错误
    }
    //普通成员方法，既可以访问 非静态成员 也可以访问静态成员
    public void ok(){
        //非静态成员
        System.out.println(n1);
        say();
        //静态成员
        System.out.println(n2);
        hi();

    }


}

```

###  VisitStatic

```java
package com.study7static_;

public class VisitStatic {
    public static void main(String[] args) {
        //类名.类变量名
        //说明：类变量是随着类的加载而创建，所以即使没有创建对象实例 也可以访问
        A a = new A();
        System.out.println(a.name);
        System.out.println(A.name);
    }
}
class A{
    //类变量
    //类变量必须遵守相关的访问权限
    public static String name="frx";
}
```

## codeblock_

### CodeBlock

```java
package com.study8codeblock_;

public class CodeBlock {
    public static void main(String[] args) {
        Move a = new Move("a");
        Move move = new Move("c", 100, "frx");


    }
}
class Move{
    private String name;
    private double price;
    private String director;
    //1 下面的三个构造器都有相同的语句
    //2  这样代码看起来比较冗余
    //3  这时我们可以吧相同的语句，放到一个代码块状中，即可
    //4  这样当我们不管调用那个构造器，创建对象，都会先调用代码块的内容
    //5  代码块 调用的顺序 优先于构造器
    {
        System.out.println("1");
        System.out.println("2");
        System.out.println("3");
    }

    public Move(String name) {
        System.out.println("Move(String name)被调用");
        this.name = name;
    }

    public Move(String name, double price) {

        this.name = name;
        this.price = price;
    }

    public Move(String name, double price, String director) {
        System.out.println("Move(String name, double price, String director)被调用");
        this.name = name;
        this.price = price;
        this.director = director;
    }

}
```

### CodeBlackDetail01

```java
package com.study8codeblock_;

public class CodeBlackDetail01 {
    public static void main(String[] args) {
        //类什么时候被加载
        //1.创建对象实例时（new)
      //  AA aa = new AA();
        //2.创建子类对象实例，父类也会加载,而且父类先加载，子类后被加载
//        BB bb=new AA();
        //3.使用类的静态成员时
//        System.out.println(Cat.n1);
         //static代码块是类加载执行，只会执行一次
//        DD dd = new DD();
//        DD dd1 = new DD();
        //普通的代码块，在创建对象实例时，会被隐式调用、
        //被创建一次 就会调用一次
        //如果只是使用类的静态成员时，普通代码块并不会执行
        System.out.println(DD.n1);//888   静态代码块会被执行
    }
}



class DD{
    public static int n1=888;
    static {
        System.out.println("DD的静态代码块1被执行");
    }
    //普通代码块 ，在new 对象时，被调用而且是创建每个对象，就调用一次
    {
        System.out.println("DD的普通代码块1被执行");

    }

}






class Cat extends Animal0 {
    public static int n1 = 99;
}
class Animal0{
    static {
        System.out.println("Animal的静态代码块1被执行");
    }


}


class AA extends BB{
    //静态代码块
    static {
        System.out.println("AA类的静态代码块1被执行...");
    }

}
class BB{
    static {
        System.out.println("BB类的静态代码块1被执行...");

    }

}
```

### CodeBlackDetail01

```java
package com.study8codeblock_;

public class CodeBlackDetail02 {
    public static void main(String[] args) {
        A a = new A();

    }
}
class A{

    static {
        System.out.println("A静态代码块01");
    }
    {
        System.out.println("A类普通代码块01");
    }
    private  int n2=getN2();

    private static int n1=getN1();
    public static int getN1(){
        System.out.println("getN1被调用..");
        return 100;
    }
    public int getN2(){
        System.out.println("getN2被调用..");
        return 200;
    }
}
//创建一个对象，在一个类中的调用顺序是
//（1）调用静态代码块和静态属性初始化（注意：静态代码块和
// 静态属性初始化调用的优先级一样，如果有多个静态代码块和
// 多个静态变量初始化，则按照他们的定义顺序调用）
//（2）调用普通代码块和普通属性的初始化（注意：普通代码块和
// 普通属性初始化调用的优先级一样，如果有多个普通代码块和
//多个普通属性初始化，则按照他们的定义顺序调用）
//（3）调用构造方法
```

### CodeBlackDetail03

```java
package com.study8codeblock_;

public class CodeBlackDetail03 {
    public static void main(String[] args) {
        new BBB();

    }
}

class AAA {
    {
        System.out.println("AAA的普通代码块..");
    }
    public AAA() {
        super();
        System.out.println("AAA() 构造器被调用");
    }


}

class BBB extends AAA {
    {
        System.out.println("BBB的普通代码块..");
    }

    public BBB() {
        //(1)  super();
        //（2）调用本类的普通代码块
        System.out.println("BBB构造器被调用..");
    }

}

```

### CodeBlackDetail04

```java
package com.study8codeblock_;

public class CodeBlackDetail04 {
    public static void main(String[] args) {
        A02 a02=new B02();
        //(1)先加载类
        //1.1先加载父类A02 再加载B02
    }
}
class A02{
    private static int n1=getVal01();
    static{
        System.out.println("A02的一个静态代码块...");//2
    }
    {
        System.out.println("A02的一个普通代码块....");//5
    }
    public int n3=getVal02();
    public static int getVal01(){
        System.out.println("getVal01");//1
        return 10;
    }
    public int getVal02(){
        System.out.println("getVal02");//6
        return 10;
    }
    public A02(){
        System.out.println("A02的构造器");//7
    }
}
class B02 extends A02{
    private static int n1=getVal03();
    static{
        System.out.println("B02的一个静态代码块...");//4
    }
    {
        System.out.println("B02的一个普通代码块....");//8
    }
    public int n4=getVal04();
    public static int getVal03(){
        System.out.println("getVal03");//3
        return 10;
    }
    public int getVal04(){
        System.out.println("getVal04");//9
        return 10;
    }
    public B02(){
        //隐藏了
        //super()
        //普通代码块
        System.out.println("B02的构造器");//10
    }
}
//(1)父类的静态代码块和静态属性
//(2)子类的静态代码块和静态属性
//(3)父类的普通代码块和普通属性初始化
//(4)父类的构造方法
//(5)子类的普通代码块和普通属性初始化
//(6)子类的构造方法

//静态代码块只能直接调用静态成员（静态属性和静态方法），
//普通代码可以调用任意成员
```

### CodeBlockExercise01



```java
package com.study8codeblock_;

public class CodeBlockExercise01 {
    public static void main(String[] args) {
        System.out.println(Person.total);
        System.out.println(Person.total);
    }
}
class Person{
    public static int total;
    static {
        total=100;
        System.out.println("in static block!");
    }
}
```

## final_

### Fianl01

```java
package com.study9final_;

public class Final01 {
    public static void main(String[] args) {

    }
}
//如果我们要求A类不能被其他类继承
//可以使用final修饰 A类
 final class A{
}
//class B extends A{
//  ×
//}
class C{
    //如果我们要求hi（）方法 不能被子类 重写
    public final void hi(){

    }
}
class D extends C{

//    public void hi() {
//        System.out.println("重写了C类的hi方法");
//    }
}
//当不希望类的某个属性的值被修改，可以用final修饰
class E{
    public  final double TAX_RATE=0.08;//加final的属性不能改
}
//当不希望某个局部变量被修改时，可以使用final修饰
class F{
    public void cry(){
       final double num=1;
       //num=2;×
    }

}

```

### FinalDetail01

```java
package com.study9final_;

public class FinalDetail01 {
    public static void main(String[] args) {
        CC cc = new CC();
         new EE().cal();
    }
}
class AA{
    //1.用final修饰的变量可以在这 （必须赋初值）
    public  final double TAX_RATE=0.08;
    public  final double TAX_RATE2;
    public  final double TAX_RATE3;
    public AA() {
        TAX_RATE2=2;//可以在构造器 里赋值
    }
    {
        TAX_RATE3=88;//可以在代码块 里赋值
    }
}
class BB{
    //如果用final修饰的属性是静态的，则初始化的位置只能是
    //1.定义时
    //2.在静态代码块 不能在构造器中赋值
    public static final double TAX_RATE=0.08;
    public static final double TAX_RATE2;
  //  public static final double TAX_RATE3;
   static  {
       TAX_RATE2=1;
    }
    public BB() {
     //  TAX_RATE3=1;×
    }
}
//final类 不能继承，但是可以实例化
final class CC{}
//如果类不是final类，但是含有final方法，则该方法不能重写，但是类可以继承
//即仍让遵守继承机制
class DD{
    public final void cal(){
        System.out.println("cal()方法");
    }
}
class EE extends DD{

}

```

### FinalDetail02

```java
package com.study9final_;

public class FinalDetail02 {
    public static void main(String[] args) {
        System.out.println(BBB.num);
        //包装类String是final类 不能被继承

    }
}
final class AAA{
    //一般来说，如果一个类已经是final类，就没有必要再将方法修饰成final方法
    public void cry(){

    }
    //final不能修饰构造方法
}
//final和static往往搭配使用，效率更高，不会导致类加载，底层编译器做了优化处理
class BBB{
    public final static int num=100;
    static {
        System.out.println("BBB静态代码块 被执行");
    }
}
```

### FinalExercise01

```java
package com.study9final_;

public class FinalExercise01 {
    public static void main(String[] args) {
        Circle circle = new Circle(6.4);
        circle.calArea();
    }
}
//final可以修饰形参
class Circle{
    private double radius;
    private final double PI;

    public Circle(double radius) {
        this.radius = radius;
      //  PI=3.14;
    }
    {
        PI=3.14;
    }
    public double calArea(){
        return PI*radius*radius;
    }
}

//final可以修饰形参
class Something{
    public int addOne(final int x){
//        ++x;×
        return x+1;
    }
}
```

## abstract_

### abstract

```java
package com.study10abstract_;

public class abstract_ {
}
abstract class Animal{
    private String name;

    public Animal(String name) {
        this.name = name;
    }
    //思考：这里eat 这里实现 没有什么意义
    //即父类方法不确定的问题
    //考虑将该方法设计为抽象方法==》abstract
    //===>所谓抽象的的方法就是没有实现
    //===>没有实现 就是没有方法体
    //===>当一个类中存在抽象方法时，需要将该类声明为abstract类
    //===>一般来说 抽象类会被继承 由子类实现抽象方法
    public abstract void eat();

}
```

### AbstractDetail01

```java
package com.study10abstract_;

public class AbstractDetail01 {
    //1抽象类不能被实例化
    //new A();×
}
//2抽象类不一定还有abstract方法，也就是说，抽象类可以没有abstract方法
//还可以有实现的方法
abstract class A{
    public void hi(){
        System.out.println("hi");
    }

}
//3一旦类包含了抽象方法，则这个类必须声明为abstract类


//4abstract只能修饰类和方法，不能修饰其他的
```

### AbstractDetail02

```java
package com.study10abstract_;

public class AbstractDetail02 {
    public static void main(String[] args) {
        System.out.println("hello");

    }
}
//5抽象类的本质还是类，所以可以有类的各种成员
abstract class D{
    public int n1=10;
    public static String name="frx";
    public void hi(){
        System.out.println("hi");
    }
    public abstract void hello();
    public static void ok(){
        System.out.println("ok");
    }
}
//7如果一个类继承了抽象类，则它必须实现抽象类的所有抽象方法，
//除非他自己也声明为abstract类
abstract class E{
    public abstract void hi();//6
}
abstract class F extends E{

}
class G extends E{
    @Override
    public void hi() {//这里想等于G子类实现了父类E的抽象方法，所谓实现方法 ，就是有语法体

    }
}
//8抽象方法不能使用private,final和static来修饰，因为这些关键字都是和重写相违背的
abstract class H{
    public abstract void hi();//抽象方法
}
```

### AbstractExercise01

```java
package com.study10abstract_.abstractexercise;

public class AbstractExercise01 {
    public static void main(String[] args) {
        Manager jack = new Manager("jack", 999, 50000);
        jack.setBonus(8000);
        jack.work();
        CommonEmployee tom = new CommonEmployee("Tom", 888, 20000);
        tom.work();
    }
}


```

#### CommonEmployee

```java
package com.study10abstract_.abstractexercise;

public class CommonEmployee extends Employee{
    public CommonEmployee(String name, int id, double salary) {
        super(name, id, salary);
    }

    @Override
    public void work() {
        System.out.println("普通员工"+getName()+"工作中..");
    }
}

```

#### Employee

```java
package com.study10abstract_.abstractexercise;

abstract public class Employee {
    private String name;
    private int id;
    private double salary;

    public Employee(String name, int id, double salary) {
        this.name = name;
        this.id = id;
        this.salary = salary;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }
    //将work()做成一个抽象方法
    public abstract void work();
}

```

#### Manager

```java
package com.study10abstract_.abstractexercise;

public class Manager extends Employee{
   private double bonus;

    public Manager(String name, int id, double salary) {
        super(name, id, salary);
    }

    public double getBonus() {
        return bonus;
    }

    public void setBonus(double bonus) {
        this.bonus = bonus;
    }

    @Override
    public void work() {
        System.out.println("经理"+getName()+"正在工作中..");

    }
}

```

## interface_

### interface01

#### Interface01

```java
package com.study11interface_.interface01;

public class Interface01 {
    public static void main(String[] args) {
        Camera camera = new Camera();
        Phone phone = new Phone();
        Computer computer = new Computer();
        computer.work(phone);//把手机接入到计算机
        System.out.println("=============");
        computer.work(camera);//把照相机接入计算机
    }
}

```

#### Camera

```java
package com.study11interface_.interface01;

public class Camera implements UsbInterface {
    @Override
    public void start() {
        System.out.println("相机开始工作");
    }

    @Override
    public void stop() {
        System.out.println("相机停止工作");
    }
}

```

#### Computer

```java
package com.study11interface_.interface01;

public class Computer {
    //编写一个方法
    public void work(UsbInterface usbInterface){
        //通过接口 来掉方法
        usbInterface.start();
        usbInterface.stop();

    }
}

```

#### Phone

```java
package com.study11interface_.interface01;

public class Phone implements UsbInterface {
    @Override
    //Phone 类实现UsbInterface
    //1.Phone类需要实现UsbInterface接口 规定/声明的方法
    public void start() {
        System.out.println("手机开始工作");

    }

    @Override
    public void stop() {
        System.out.println("手机停止工作");
    }
}

```

#### UsbInterface

```java
package com.study11interface_.interface01;

public interface UsbInterface {//接口
    //规定接口的方法
    public void start();
    public void stop();
}

```

### interface02

#### AInterface

```java
package com.study11interface_.interface02;

public interface AInterface {
    //写属性
    public int n1=10;
    //写方法
    //在接口中 抽象方法可以省略abstract关键字
   //1. public void hi();
    //在jdk8之后，可以有默认实现方法  但是需要default关键字修饰
    //2. 默认实现方法
    default public void ok(){
        System.out.println("ok....");
    }
    //3.在jdk8之后，可以有静态方法
    public static void cry(){
        System.out.println("cry....");
    }
}

```

#### Interface02

```java
package com.study11interface_.interface02;

public class Interface02 {
    public static void main(String[] args) {

    }
}
//1.如果一个类 implements实现接口
//2.需要该将接口的所有抽象方法都实现
class A implements AInterface{
    public void hi() {
        System.out.println("hi....");

    }
}
```

### interface03

#### DBInterface

```java
package com.study11interface_.interface03;

public interface DBInterface {//项目经理
    public void connect();//连接方法
    public void close();//关闭方法
}

```

#### Interface03

```java
package com.study11interface_.interface03;

public class Interface03 {
    public static void main(String[] args) {
        MysqlDB mysqlDB = new MysqlDB();
        t(mysqlDB);
        OracleDB oracleDB = new OracleDB();
        t(oracleDB);
    }
    public static void t(DBInterface db){
        db.connect();
        db.close();

    }

}

```

#### MysqlDB

```java
package com.study11interface_.interface03;

public class MysqlDB implements DBInterface{
    @Override
    public void connect() {
        System.out.println("连接MySQL");

    }

    @Override
    public void close() {
        System.out.println("关闭MySQL");

    }
}

```

#### OracleDB

```java
package com.study11interface_.interface03;

public class OracleDB implements DBInterface{
    @Override
    public void connect() {
        System.out.println("连接oracle");
    }

    @Override
    public void close() {
        System.out.println("关闭close");
    }
}

```

### interface04

#### ExtendsVSInterface

```java
package com.study11interface_.interface04;

public class ExtendsVSInterface {
    public static void main(String[] args) {
        LittleMonkey littleMonkey = new LittleMonkey("悟空");
        littleMonkey.climbing();
        littleMonkey.swimming();
        littleMonkey.fly();

    }
}
//接口
interface Fishable{
    void swimming();
}
interface Birdable{
    void fly();
}








//猴子
class Monkey{
    private String name;

    public Monkey(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void climbing(){
        System.out.println("猴子会爬树...");
    }
}
//继承
//小结：当子类继承了父类，就自动拥有父类的功能
////如果子类需要扩展功能 可以通过实现接口的方式扩展
//可以理解实现接口是对java单继承机制的一种补充




class LittleMonkey extends Monkey implements Fishable,Birdable{
    public LittleMonkey(String name) {
        super(name);
    }

    @Override
    public void swimming() {
        System.out.println(getName()+"通过学习，可以向小鱼儿一样游泳..");
    }

    @Override
    public void fly() {
        System.out.println(getName()+"通过学习，可以向鸟儿一样飞翔...");
    }
}
```

#### InterfaceExercise01

```java
package com.study11interface_.interface04;

public class InterfaceExercise01 {
    public static void main(String[] args) {
        B b = new B();
        System.out.println(b.a);
        System.out.println(AA.a);
        System.out.println(B.a);
    }
}
interface AA{
    int a=23;
}
class B implements AA{

}
```

####  InterfaceExercise02

```java
package com.study11interface_.interface04;

public class InterfaceExercise02 {
    public static void main(String[] args) {
        new C().pX();

    }
}
interface A{
int x=0;
}
class BB{
    int x=1;
}
class C extends BB implements A{
    public void pX(){
//        System.out.println(x);//原因不明确
        //访问接口的x就使用A.x
        //访问父类的x就使用super.x
        System.out.println(A.x);
        System.out.println(super.x);
    }

}
```

#### InterfacePolyArr

```java
package com.study11interface_.interface04;

public class InterfacePolyArr {
    public static void main(String[] args) {
        //多态数组(接口类型数组
        USB usb[]=new USB[2];
        usb[0]=new Phone_();
        usb[1]=new Camera_();


        for (int i = 0; i < usb.length; i++) {
            usb[i].work();//动态绑定
            if(usb[i] instanceof Phone_){
                ( (Phone_)usb[i]).cal();
            }
        }



    }
}
interface USB{
   void work();
}
class Phone_ implements USB{



    public void cal() {
        System.out.println("手机可以打电话....");
    }

    @Override
    public void work() {
        System.out.println("手机工作中....");
    }
}
class Camera_ implements USB{

    @Override
    public void work() {
        System.out.println("相机工作中....");
    }
}
```

#### InterfacePolyParameter

```java
package com.study11interface_.interface04;

public class InterfacePolyParameter {
    public static void main(String[] args) {
        //接口的多态
        //接口类型的变量if01可以指向实现了IF接口的类的对象实例
        IF if01=new Monster();
        if01=new Car();
        //继承体现的多态
        //父类类型的变量a可以指向继承AAA的子类实例
        AAA a=new BBB();
        a=new CCC();

    }
}

interface IF{

}
class Monster implements IF{

}
class Car implements IF{

}
class AAA{

}
class BBB extends AAA {}
class CCC extends AAA{}
```

#### InterfacePolyPass

```java
package com.study11interface_.interface04;
/*
演示多态传递现象
 */
public class InterfacePolyPass {
    public static void main(String[] args) {
        //接口类型的变量可以指向，实现了该类的对象实例
        IG ig=new Teacher();
        //如果IG继承了IH的接口，而Teacher实现了IG接口
        //那么。实际相当于Teacher类实现了IH接口
        //这就是所谓的多态接口
        IH ih=new Teacher();

    }
}
interface IH{
    void hi();

}
interface IG extends IH{

}
class Teacher implements IG{

    @Override
    public void hi() {

    }
}
```

## innerclass_

### InnerClass01

```java
package com.study12.innerclass_;

public class InnerClass01 {//外部其他类
    public static void main(String[] args) {

    }
}
class Outer{//外部类
    private int n1=100;

    public Outer(int n1) {
        this.n1 = n1;
    }

    public void m1(){
        System.out.println("m1方法");
    }
    {//代码块
        System.out.println("代码块....");
    }
    class Inner{//内部类,在Outer类的内部


    }
}
```

### LocalInnerClass

```java
package com.study12.innerclass_;
/*
演示局部内部类的使用
 */
public class LocalInnerClass {
    public static void main(String[] args) {
        //演示一把
        Outer2 outer2 = new Outer2();
        outer2.m1();
        System.out.println("Outer02的HashCode="+outer2.hashCode());

    }
}
class Outer2{//外部类
    private int n1=100;
    private void m2(){//私有方法
        System.out.println("Outer02 m2");
    }
    public void m1(){//方法
        //1.局部内部类是定义在外部类的局部位置上，通常在方法 或代码块中
        //3.局部内部类不能添加访问修饰符，但是可以添加final修饰
        //4.作用域：仅仅在定义它的方法或代码块中
        String name="XXX";
        class Inner02{//局部内部类(本之仍然是一个类）
            //2.可以访问外部类的所有成员，包括私有的
            private int n1=200;
            public void f1(){
                //5.局部内部类可以直接访问外部类的成员 比如 下面的n1和 m2方法
                //7.如果外部类和局部内部类的成员重名时，默认遵守就近原则，如果想访问
//                外部类的成员，则可以使用(外部类名.this.成员)去访问
                //Outer.this是外部类的一个对象，即哪个对象调用了m1，Outer02.this就指向了哪个对象
                System.out.println("n1="+n1+"   外部类的n1="+Outer2.this.n1);
                System.out.println("Outer.this hashCode="+Outer2.this.hashCode());
                m2();

            }

        }
        //6.外部类在方法中，可以创建 Inner02对象，然后调用方法
        Inner02 inner02 = new Inner02();
        inner02.f1();
        class Inner03 extends Inner02{

        }

    }
    {//代码块
         class Inner04{

         }

    }

}
```

### MemberInnerClass

```java
package com.study12.innerclass_;

public class MemberInnerClass {
    public static void main(String[] args) {
        Outer08 outer08 = new Outer08();
        outer08.t1();

        //外部其他类 使用成员内部类的两种方式
        //第一种方式
        //outer08.new Inner08();相当于把 new Inner08()当做是outer08的成员
        //这就是一个语法
        Outer08.Inner08 inner08 = outer08.new Inner08();
        inner08.say();
        //第二方式 在外部类中 编写一个方法 可以返回Inner08的对象
        Outer08.Inner08 inner08Instance = outer08.getInner08Instance();
        inner08Instance.say();



    }
}
class Outer08{

    private int n1=10;
    public String name="张三";
    //1.成员内部类是定义在外部类的成员位置上
    //2.可以添加任意访问修饰符(public protected默认 private)

    private  void hi(){
        System.out.println("hi方法..");
    }
    class Inner08{//成员内部类
        public double salary=99.9;
        private int n1=66;
        public void say(){
            //可以直接访问外部类的所有成员，包含私有的
            //如果成员内部类的成员 和外部类的成员重名了 遵守就近原则
            //可以通过 外部类名.this.属性 来访问外部类的成员
            System.out.println("n1="+n1+"name="+name+"外部类的n1"+Outer08.this.n1);
            hi();

        }
    }
    //方法 返回一个Inner08实例
    public Inner08 getInner08Instance(){
        return new Inner08();
    }
    //写方法
    public void t1(){
        //使用了成员内部类
        //外部类使用成员内部类 创建成员内部类的对象 然后使用相关的方法
        Inner08 inner08 = new Inner08();
        inner08.say();
        System.out.println(inner08.salary);
    }


}
```

### StaticInnerClass01

```java
package com.study12.innerclass_;

public class StaticInnerClass01 {
    public static void main(String[] args) {
        Outer10 outer10 = new Outer10();
        outer10.m1();
        //外部其他类 使用静态内部类
        //方式一
        Outer10.Inner10 inner10 = new Outer10.Inner10();//考虑访问权限
        inner10.say();
        //方式二
        Outer10.Inner10 inner101 = outer10.getInner10();
        System.out.println("===============");
        inner10.say();
        Outer10.Inner10 inner102 = outer10.getInner10();
        System.out.println("===============");
        Outer10.getInner10_();
        inner102.say();



    }
}
class Outer10{//外部类
    private int n1=10;
    private static  String name="张三";
    //Inner10就是静态内部类
    //1.放在外部类的成员位置
    //2.使用static修饰
    //3.可以访问外部的类的所有静态成员，包含私有的，但不能直接访问非静态成员
    //4.可以添加任意访问修饰符(public protected 默认 private)因为他的地位就是一个成员
    //5.作用域：同其他成员，为整个类体
      static class Inner10{
        private String name="frx";
        public void say() {
            System.out.println(name+"   外部类name="+Outer10.name);
        }

    }
    public void m1(){//外部类访问内部类 创建对象 访问
        Inner10 inner10 = new Inner10();
        inner10.say();
    }
    public Inner10 getInner10(){
        return new Inner10();
    }
    public static Inner10 getInner10_(){
          return new Inner10();
    }
}
```

### AnonymousInnerClass

```java
package com.study12.innerclass_;

/*
演示匿名内部类的使用
 */
public class AnonymousInnerClass {
    public static void main(String[] args) {
        Outer04 outer04 = new Outer04();
        outer04.method();

    }
}
class Outer04{
    private int n1=10;//属性
    public void method(){//方法
        //基于接口的匿名内部类
        //1.想使用IA，并创建对象
        //2.传统方式，写一个类，实现该接口，并创建对象
        //3.需求 Tiger类只是使用一次，后面再不使用
        //4.可以使用匿名内部类来简化开发
        //5.tiger的编译类型？IA
        //5.tiger的运行类型？就是匿名内部类
//        class XXXX implements IA{
//
//            @Override
//            public void cry() {
//                System.out.println("老虎叫唤");
//            }
//        }
        //7.在jdk的底层，在创建匿名内部类 Outer04$1,立马就创建了Outer04$1的实例，并且把地址返回给
        //tiger
        //8.匿名内部类使用一次 就不能使用
        IA tiger= new IA() {
             @Override
             public void cry() {
                 System.out.println("老虎叫唤...");

             }
         };
        System.out.println("tiger的运行类型为"+tiger.getClass());
        tiger.cry();
        //        IA tiger = new Tiger();
//        tiger.cry();

        //演示基于类的匿名内部类
        //分析
        //1.father 编译类型 Father
        //2.father  运行类型为 Outer04$2
        //4.底层会创建匿名内部类
        //4.同时也返回了匿名内部类的对象
       Father father= new Father("Jack"){
           @Override
           public void Test() {
               System.out.println("匿名内部类 重写了test方法");
           }
       };
        System.out.println("father的运行类型为"+father.getClass());
        father.Test();
       //基于抽象类的匿名内部类
       Animal animal= new Animal(){
            @Override
            void eat() {
                System.out.println("小狗吃骨头....");
            }
        };
       animal.eat();


    }
}
interface IA{//接口
    public void cry();
}


//class Tiger implements IA{
//
//    @Override
//    public void cry() {
//        System.out.println("老虎叫唤...");
//    }
//}
//class Dog implements IA{
//
//    @Override
//    public void cry() {
//        System.out.println("小狗汪汪...");
//    }
//}
class Father{//类
    public Father(String name) {
        System.out.println("接收到name="+name);
    }
    public void Test(){

    }
}
abstract class Animal{
    abstract void eat();

}
```

### AnonymousInnerClassDetail

```java
package com.study12.innerclass_;

public class AnonymousInnerClassDetail {
    public static void main(String[] args) {
        Outer05 outer05 = new Outer05();
        outer05.f1();
        //外部其他类 不能访问匿名内部类
        System.out.println("main类 outer05的hashcode="+outer05.hashCode());

    }
}
class Outer05{
    private int n1=99;
    public void f1(){
        //创建一个基于类的匿名内部类
        //不能添加访问修饰符，因为他的地位就是一个局部变量
        //作用域 ：仅仅在定义它的方法或代码块中
         Person p=new Person(){
             private int n1=88;
            @Override
            public void hi() {
                System.out.println("匿名内部类 重写了hi()方法  n1="+
                        n1+"   外部类的n1="+Outer05.this.n1);
                //Outer05.this 就是调用f1的对象
                System.out.println("Outer05.hashCode="+Outer05.this.hashCode());
            }
        };
         p.hi();//动态绑定，运行类型是 Outer05$1
        //也可以直接调用，匿名内部类本身也是返回对象
        new Person(){
            @Override
            public void hi() {
                System.out.println("匿名内部类 重写了hi()方法 哈哈...");
            }

            @Override
            public void OK(String str) {
                System.out.println("OK");
            }
        }.OK("Jack");
    }
}
class Person{//类
    public void hi(){
        System.out.println("Person hi");
    }
    public void OK(String str){
        System.out.println("Person OK");

    }
}

```

### InnerClassExercise01

```java
package com.study12.innerclass_;

public class InnerClassExercise01 {
    public static void main(String[] args) {


       f1(new IL() {//1
            @Override
            public void show() {
                System.out.println("这是一幅名画");
            }
        });
        f1(new Picture(){//2
        });

    }


    //静态方法,形参是接口类型
    public static void f1(IL il){
        il.show();


    }
}

//接口
interface IL{
    void show();
}
//类 实现IL
class Picture implements IL{//2
    @Override
    public void show() {
        System.out.println("这是一幅名画");

    }
}
```

### InnerClassExercise02

```java
package com.study12.innerclass_;

public class InnerClassExercise02 {
    public static void main(String[] args) {
        CellPhone cellPhone = new CellPhone();
        //1.传递的是实现了Bell 接口的匿名内部类
        //2.重写了ring方法
        //3.bell=new Bell() {
        //            @Override
        //            public void ring() {
        //                System.out.println("懒猪起床了");
        //            }
        //        });
        cellPhone.alarmClock(new Bell() {
            @Override
            public void ring() {
                System.out.println("懒猪起床了");
            }
        });
        cellPhone.alarmClock(new Bell() {
            @Override
            public void ring() {
                System.out.println("小伙伴上课");
            }
        });
    }
}

interface Bell {
    void ring();
}
class CellPhone{//类
    public void alarmClock(Bell bell){//形参Bell是接口类型
        System.out.println(bell.getClass());
        bell.ring();//动态绑定
    }

}
```

## singel_

### SingleTon1

```java
package com.single_;

public class SingleTon1 {
    public static void main(String[] args) {
//通过方法获取对象
//        GirlFriend instance=GirlFriend.getInstance();
//        System.out.println(instance);
//        GirlFriend instance2=GirlFriend.getInstance();
//       on System.out.println(instance2);
//        System.out.println(instance==instance2);//T
        System.out.println(GirlFriend.n1);
    }
}
//有一个类
class GirlFriend{
    public static int n1=100;
    private String name;
    //饿汉式可能创建了对象 但没有使用
    //为了能在静态方法中，返回gf对象，需要将其修饰为static
    private static GirlFriend gf=new GirlFriend("小红");

    //如何保证我们只能创建一个GirlFriend对象
    //1.将构造器私有化
    //2.在类的内部直接创建
    //3.提供一个公共的静态方法 返回gf对象
    private GirlFriend(String name) {
        System.out.println("构造器被调用");
        this.name = name;
    }
    public static GirlFriend getInstance(){
        return gf;
    }

    @Override
    public String toString() {
        return "GirlFriend{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

### SingleTon2

```java
package com.single_;

public class SingleTon2 {
    public static void main(String[] args) {
       // System.out.println(Cat.n1);
        Cat instance=Cat.getInstance();
        System.out.println(instance);
        //再次调用getInstance
        Cat instance2=Cat.getInstance();
        System.out.println(instance2);
        System.out.println(instance=instance2);//T
    }
}
//希望在程序运行过程中，只能创建一个Cat对象

class Cat {
    private String name;
    public static int n1=999;
    private static Cat cat;
    //1.将构造器私有化
    //2.定义一个静态属性
    //3.提供一个Public的static方法，可以返回一个Cat对象
    //4.懒汉式，只有当用户使用getInstance时，才返回Cat对象，
    //后面再次调用时，会返回上次创建的Cat对象
    //从而保证了单例
    private Cat(String name) {
        System.out.println("构造器被调用..");
        this.name = name;
    }
    public static Cat getInstance(){
        if(cat==null){
            cat=new Cat("小可爱");
        }
        return cat;
    }

    @Override
    public String toString() {
        return "Cat{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

## smallchange

### SmallChangeSysApp

```java
package com.smallchange.oop;
/*
这里我们直接调用SmallChangeSysOOP对象，显示主菜单 即可1
 */
public class SmallChangeSysApp {
    public static void main(String[] args) {
        System.out.println("====hello====");
        new SmallChangeSysOOP().mainMenu();
    }
}

```

### SmallChangeSysOOP

```java
package com.smallchange.oop;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;

/*
该类是完成零钱通的各个功能
使用OOP（面向对象编程）
将各个功能对应一个方法
 */
public class SmallChangeSysOOP {
    //属性...
    //定义相关的变量
    boolean loop = true;
    Scanner scanner=new Scanner(System.in);
    String  key="";
    //2.完成零钱通思路
    //（1）可以 把收益入账和消费，保存到数组（2）可以使用对象（3）简单的话可以使用String拼接
    String details="-----------------------OOP零钱通明细---------------------";
    //3.完成收益入账  完成功能驱动程序员新的变化和代码
    //定义新的变量
    double money=0;
    double balance=0;
    Date date=null;//date是java.util.Date类型，表示日期
    SimpleDateFormat sdf=new SimpleDateFormat("yyyy-MM-dd HH:mm");//可以用于日期格式化的
    //4.消费
    //定义新变量，保存消费的原因
    String note;
    public void mainMenu(){
        do{
            System.out.println("\n===================选择零钱通菜单===================");
            System.out.println("\t\t\t1 零钱通明细");
            System.out.println("\t\t\t2 收益入账");
            System.out.println("\t\t\t3 消费");
            System.out.println("\t\t\t4 退    出");
            System.out.print("请选择（1-4）：");
            key=scanner.next();
            //使用switch分支 控制
            switch (key){
                case "1":
                   this.detail();
                   break;
                case "2":
                    this.income();
                    break;
                case "3":
                    this.pay();
                    break;
                case "4":
                   this.exit();
                    break;
                default:
                    System.out.println("选择有误，请重新选择");

            }

        }while (loop);

    }
    //完成零钱通明细
    public void detail(){
        System.out.println(details);

    }
    //完成收益入账
    public void income() {
        System.out.print("收益入账金额：");
        money = scanner.nextDouble();
        //money的值范围应该校验一下
        //思路 找出不正确的金额条件，然后给出提示，就直接return
        if (money <= 0) {
            System.out.println("收益金额需要大于0");
            return;//退出方法，不再执行后面的代码
        }

        balance += money;
        //拼接收益入账信息到 details
        date = new Date();//获取当前日期
        System.out.println(sdf.format(date));
        details += "\n收益入账\t" + money + "\t" + sdf.format(date) + "\t" + balance;
        //消费

    }
        public void pay(){
            System.out.print("消费金额：");
            money=scanner.nextDouble();
            ////money的值范围应该校验一下
            //找出金额不正确的情况，
            if(money<=0||money>balance){
                System.out.println("你的消费金额应该在0-"+balance);
                return;
            }
            System.out.print("消费说明:");
            note=scanner.next();
            balance-=money;
            //拼接消费信息到 details
            date =new Date();//获取当前日期
            System.out.println(sdf.format(date));
            details+="\n"+note+"\t"+money+"\t"+sdf.format(date)+"\t"+balance;
        }
        //退出..
    public void exit() {
        //用户输入4退出时，确定一下是否退出y/n 必须输入正确的y/n
        //否则循环输入执行，直到输入y或者n
        //思路分析：
        //(1)定义一个变量 choice，接受用户的输入
        //(2)使用while+break，来处理接受到输入y或者n
        //(3)退出while后，再判断choice是y还是n，就可以决定是否退出
        //(4)建议一段代码，完成一个小功能，尽量
        String choice = "";
        while (true) {
            System.out.println("你确定要退出吗？y/n");
            choice = scanner.next();
            if ("y".equals(choice) || "n".equals((choice))) {
                break;
            }
        }
        //当用户退出while，进行判断
        if (choice.equals("y")) {
            loop = false;
        }
    }
    }


```







