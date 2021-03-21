# java03

## Object01

```java
package day03;
public class Object01 {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		//第一只猫的信息
	/*	String cat1Name="小白";
		int cat1Age =3;
		String cat1Color ="白色";
		//第二只猫的信息
		String cat2Name ="小花";
		int cat2Age=100;
		String cat2Color="花色";
	//用数组来表示	
		String[] cat1= {"小白","3","白色"};
		String[] cat2= {"小花","100","花色"};*/
		/*1类是抽象的，概念的，代表一类事物，比如人类，猫类..，即它是数据类型。
		 *2对象是具体的，实际的，代表一个具体事物，即是实例。
		 *3类是对象的模板，对象是类的一个个体，对应一个实例	
		*/
		
		//1. new Cat()创建一个猫(猫对象)
		//2.Cat cat1=new Cat;把创建的猫赋给 cat1
	    //3.cat1就是一个对象
		Cat cat1=new Cat();
		cat1.name="小白";
		cat1.age=3;
		cat1.color ="白色";
		//创建了第二只猫，并赋给 cat2
		//cat2 也是一个对象（猫对象）
		Cat cat2=new Cat();
		cat2.name="小花";
		cat2.age=100;
		cat2.color="花色";
		//怎么访问对象的属性呢
		System.out.println("第一只猫的信息"+cat1.name+" "+cat1.age+" "+cat1.color);
		System.out.println("第二只猫的信息"+cat2.name+" "+cat2.age+" "+cat2.color);
		}
	}
	//定义一个猫类Cat->自定义的数据类型
class Cat{
	//属性
	String name;//名字
	int age;//年龄
	String color;//颜色

	}



```

## Object02

```java
package day03;

public class Object02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}

}
class Car{
	String name;//属性，成员变量，字段field
	double peice;
	String color;
	String[] master;//属性可以是基本数据类型，也可以是引用数据类型（对象，数组)。
	
}
```

## Object03

```java
package day03;

public class Object03 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		// Person p1=new Person();
		// p1.age=10;
		// p1.name="小明";
		// Person p2=p1;//p1赋值给了p2
		// System.out.println(p2.age);
		Person a = new Person();
		a.age = 10;
		a.name = "小明";
		Person b;
		b=a;
		System.out.println(b.name);
		b.age=200;
		b=null;
		System.out.println(a.age);
		//System.out.println(b.age);//出现异常
	}

}

class Person {
	int age;
	String name;

}

```

## PropertiesDetail

```java
package day03;

public class PropertiesDetail {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//p1 是对象名（对象引用）
		//newPerson()创建的对象空间（数据)才是真正的对象
		Person0 p1=new Person0();
		//对象得属性默认值，遵守数组规则：
		//int 0,short 0,byte 0,long 0,float 0.0,double 0.0,char \u0000,boolean
        System.out.println("\n当前这个人的信息");
        System.out.println("age="+p1.age+"name="
        		+p1.name+"sal="+p1.sal+"isPass"+p1.isPass);
	}

}
class Person0{
	int age;
	String name;
	double sal;
	boolean isPass;
	
}

```

