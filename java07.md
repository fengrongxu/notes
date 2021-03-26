# java07

## Homework01

```java
package day08;
import java.util.Scanner;

import day08.A01;

public class Homework01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        A01 a01=new A01();
        double arr[]=new double[5];//{}
        for(int j=0;j<arr.length;j++) {
        	 Scanner input =new Scanner(System.in);
        	 arr[j]=input.nextDouble();
        } 
        Double res=a01.max(arr);
        if(res!=null) {
        System.out.println("arr的最大值="+res);
	}else {
		System.out.println("arr输入有误");
	}
	}
}
/*
 编写一个类A01，定义方法max，实现求某个double数组的最大值，并返回
 形参（double arr[]) */
class A01{
	public double max(double arr[]) {
		//先判断 arr是否为空
		//至少保证arr有一个元素
		if(arr!=null&&arr.length>0) {
		double max=arr[0];
		for(int i=0;i<arr.length;i++) {
			if(arr[i]>max) {
				max=arr[i];
			}
		}
		return max;//double 值
	}else {
		return (Double) null;
	}
}
}

```

## Homework02

```java
package day08;

public class Homework02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
       String strs[]= {"jack","tom","mary","milan"};
       A02 a02=new A02();
       int index=a02.find("milan", strs);
       System.out.println("查找的index="+index);
	}

}
/*
 编写类A02，定义方法find，实现查找某字符串是否在字符串数组中。
 并返回索引，如果找不到，返回-1
 返回值 int 形参(String,String[])
  */
class A02{
	public int find(String findStr,String strs[]) {
		//直接遍历
		for(int i=0;i<strs.length;i++) {
			if(findStr.equals(strs[i])) {//
				return i;
			}
		}
		return -1;
	}
}
 

```

## Homework03

```java
package day08;

public class Homework03 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
          Book book=new Book("笑傲江湖",30);
          book.info();
          book.updayePrice();//更新价格
          book.info();
          
	}

}
/*
 * 编写Book，定义方法updatePrice，实现更改某本书的价格，具体：如果价格
 * 》150，则更改为150，如果价格>100,更改为100，否则不变
 * 分析
 * 1.类名 Book
 * 2.属性  price，name
 * 3.方法名 updatePrice
 * 4.形参
 * 5返回值 void
 */
class Book{
	String name;
	double price;
	public Book(String name,double price) {
		this.name=name;
		this.price=price;	
	}
	public void updayePrice() {
		if(this.price>150) {
			this.price=150;
		}else if(this.price>100) {
			this.price=100;
		}
		
	}
	//显示书籍情况
	public void info() {
		System.out.println("书名="+this.name+"   价格="+this.price);
	}
	
	
}

```

## Homework04

```java
package day08;

public class Homework04 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int oldArr[]= {10,30,50};
		A03 a03=new A03();
		a03.copyArr(oldArr);
		int newArr[]=a03.copyArr(oldArr);
		System.out.println("返回的newArr元素情况");
		for(int i=0;i<newArr.length;i++) {
		System.out.print(newArr[i]+"\t");
		
		}

	}

}
/*
 编写类A03，实现数组的复制功能copyArr,
 输入旧数组，返回一个新数组元素和旧数组一样
  */
class A03{
	public int[] copyArr(int oldArr[]) {
		int newArr[]=new int[oldArr.length];//在堆中创建一个长度为oldArr
	//	.length数组
		for(int i=0;i<oldArr.length;i++) {
			newArr[i]=oldArr[i];	
		}
		return newArr;
	}
}
```

## Homework05

```java
package day08;

public class Homework05 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
           Circle circle= new Circle(3.0);
           System.out.println("面积="+circle.area());
           System.out.println("周长="+circle.len());
	}
/*编写一个圆类Cricle，定义属性：半径，提供显示圆周长功能的方法
 * 提供显示圆面积的方法
 */
}
class Circle{
	double radius;
	public Circle(double radius) {
		this.radius=radius;
	}
	public double area() {
		return Math.PI*radius*radius;
	}
	public double len() {
		return 2*Math.PI*radius;
	}
	}

```

## Homework06

```java
package day08;

public class Homework06 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
       Cale cale=new Cale(2,10);
       System.out.println("和="+cale.sum());
       System.out.println("差="+cale.minus());
       System.out.println("乘="+cale.mul());
       Double divRes=cale.div();
       if(divRes!=null) {
       System.out.println("除="+cale.div());
       }
	}

}
/*
 编程创建一个Cale计算类，在其中定义2个变量表示连个操作数
 定义四个方法实现和、差、乘、商（要求除数为0的话，要提示）
 并创建两个对象，分别测试
 */
class Cale{
	double num1;
	double num2;
	public Cale(double num1,double num2) {
		this.num1=num1;
		this.num2=num2;	
	}
	//和
	public double sum() {
		return num1+num2;
	}
	//差
	public double minus() {
		return num1-num2;
	}
	//乘积
	public double mul() {
		return num1*num2;
	}
	//除法
	public Double div() {
		//判断
		if(num2==0) {
			System.out.println("除数不能为0");
			return  null;
		}else {
		return num1/num2;
	}
}
}
```

## Homework07

```java
package day08;

public class Homework07 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        Dog dog=new Dog("小黄","白色",20);
        dog.show();
	}

}
class Dog{
       String name;
       String color;
       int age;
	public Dog(String name,String color,int age) {
		this.name=name;
		this.color=color;
		this.age=age;
		}
		public void show(){
			System.out.println("这个狗的名字为"+this.name+" 颜色为"+this.color+" 年龄为 "+this.age);
		}
		
	}

```

## Test

```java
package day08;

public class Test{//公开类
	int count=9;//属性
	
	public void count1() {//Test类的成员方法
		count=10;//这个count就是属性 改成10
		System.out.println("count1="+count);
	}
	public void count2() {//Test累的成员方法
		System.out.println("count1="+count++);
	}
	//这是Test类的main方法，任何一个类，都可能有main
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//.new Test()是匿名对象（在堆里面）只能使用一次
		//new Test().count1()创建好匿名对象后，就调用count1（）
       new Test().count1();
       Test t1=new Test();
       t1.count2();
       t1.count2();
	}
}

```

## Homework09

```java
package day08;

public class Homework09 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Music music =new Music("笑傲江湖",300);
		music.play();
		System.out.println(music.getInto());
	}

}
/*
 定义Music类，里面含有音乐名name，音乐时长times属性
 并有播放play功能和返回本身属性信息的功能方法getInfo
 */
class Music{
	String name;
	int times;
	public Music(String name,int times) {
		this.name=name;
		this.times=times;
	}
	//播放play功能
	public void play() {
		System.out.println("音乐 "+name+"正在播放中...时长为"+times+"秒");
	}
	//返回本身属性信息的功能方法getInto
	public String getInto() {
		return "音乐"+name+"播放时间为"+times;
	}
}
```

## Homework10

```java
package day08;

public class Homework10 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Demo d1=new Demo();
		Demo d2=d1;
		d2.m();
		System.out.println(d1.i);//101
		System.out.println(d2.i);//101
	}

}
class Demo{
	int i=100;
	public void m() {
		int j=i++;
		System.out.println("i="+i);//101
		System.out.println("j="+j);//100
	}
}


```

## Homework11

```java
package day08;

public class Homework11 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}
}
/*
 创建一个Employee类
 属性有（名字，性别，年龄，职位，薪水），提供3个构造方法。可以初始化
 （1）（名字，性别，年龄，职位，薪水），
 （2）（名字，性别，年龄）
 （3）（职位，薪水），要求充分服用构造器
  */
class Employee{
	//名字，性别，年龄，职位,薪水
	String name;
	char gender;
	int age;
	String job;
	double sal;
	//因为要求可以服用 构造器，先写属性少的构造器
	//职位，薪水
	public Employee(String job,double sal) {
		this.job=job;
		this.sal=sal;
	}
	//名字，性别，年龄
	public  Employee(String name,char gender,int age) {
		this.name=name;
		this.gender=gender;
		this.age=age;
	}
	//职位，薪水，名字，性别，年龄
	public Employee(String job,double sal,String name,char gender,int age) {
		this(name,gender,age);//使用到前面的构造器
		this.job=job;
		this.sal=sal;
		
	}
}
```

## Homework13

```java
package day08;

public class Homework13 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Circle1 c=new Circle1();
		PassObject po=new PassObject();
        po.printAreas(c, 5);
	}

}
/*
(1)定义一个Circle1类，包含一个double型的radius属性代表圆的半径，findArea（）
返回圆的面积。
（2）定义一个类PassObject，在类中定义一个方法printArea（）
该方法的定义如下：
public void printAreas(Circle c,int times)
(3)在printArea方法中打印输出1到times之间的的每个整数半径值，
以及对应的面积。列如，times为5，则输出半径为1,2,3,4,5以及对应的面积
（4）在main方法中调用printAreas（）方法，调用完毕后输出当前半径值。

 */
class Circle1{//类
	double radius;//半径
	public  Circle1() {//无参构造器
		
	}
	public Circle1(double radius){
		this.radius=radius;
	}
	public double findArea(){
		return Math.PI*radius*radius;
	}
	//添加方法setRadius,修改对象的半径值
	public void setRadius(double radius) {
		this.radius=radius;
	}
}
class PassObject{
	public void printAreas(Circle1 c,int times) {
		System.out.println("radius\tarea");
		for(int i=1;i<=times;i++) {//输出1到times之间的每个整数半径值
			c.setRadius(i);//修改c对象的半径值
			System.out.println(i+"\t"+c.findArea());
			
		}
	}
	
}
```

