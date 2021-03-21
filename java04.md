# Java03

## Method01

```java
package day04;

public class Method01 {

	public static void main(String[] args) {
		// 方法使用
		// 1.方法写好后，如果不去调用，不会输出
		// 2.先创建对象，然后调用方法即可
		Person p1=new Person();
		p1.speak();//调用方法
		p1.cal01();//调用cal01
		p1.cal02(10);//调用cal02
		//调用getSum方法，同时num1=10，num2=20
		//把方法getSum返回的值，赋给变量returnRes
		int returnRes =p1.getSum(10,20);
		System.out.println("getSum方法返回的值="+returnRes);
	}	
}
class Person{
	String name;
	int age;
	//方法（成员方法）
	//添加speak 成员方法，输出“我是一个好人”
	//老韩解读
	//1.public 表示方法是公开的
	//2.void:表示方法没有返回值
	//3.speak():speak是方法名； （）形参列表
	//4.{}方法体，可以写我们要执行的代码
	//5.System.out.println（"我是一个好人");表示我们的方法就是输出一句话
	
   public void speak() {
	   System.out.println("我是一个好人");
	   }
   //添加cal01 成员方法，可以计算从1+...+1000的结果
   public void cal01(){
	   //循环完成
	   int res =0;
	   for(int i=1;i<=1000;i++) {
		   res+=i;
	   }
	   System.out.println("计算结果="+res);
   }
   //添加cal02的方法，该方法可以接受一个数n，计算从1+..+n的结果
   //老韩解读
   //1.（int n）形参列表，表示当前有一个形参n，可以接受用户输入
   public void cal02(int n){
	   int res =0;
	   for(int i=1;i<=n;i++) {
		   res+=i;
	   }
	   System.out.println("cal02的计算结果="+res);
	   
   }
   //添加getSum成员方法，可以计算两个数的和
   //老韩解读
   //1.public表示方法是公开的
   //2.int:表示方法执行后，返回一个int值
   //3.getSum方法名
   //4.(int num1,int num2）形参列表，2个形参，可以接受用户传入的两个数
   //5.return res;表示把res的值，返回
   public int getSum(int num1,int num2){
	   int res =num1+num2;
	   return res;
	   
   }
   }
   //方法调用小结
/*
 *1.当程序执行到方法时，就会开辟一个独立的空间（栈空间)
 *2.当方法执行完毕，或者执行到return语句时，就会返回；
 *3.返回到调用方法的地方
 *4.返回后，继续执行方法后面的代码
 *5.当main（）方法（栈）执行完毕，整个程序退出
 * 
 * 
 * 
 * 
 * 
 * 
 * */

```

## Method02

```java
package day04;

public class Method02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        int [][]map= {{0,0,1},{1,1,1},{1,1,3}};
        //使用方法完成数组
        MyTools too1=new MyTools();
        too1.printArr(map);
        too1.printArr(map);
        too1.printArr(map);
        
        //遍历map数组
        //传统的解决方式就是直接执行
//        for(int i=0;i<map.length;i++) {
//        	for(int j=0;j<map[i].length;j++) {
//        		System.out.print(map[i][j]+" ");
//        	}
//        	System.out.println();
//        }
        //....
        //
        //要求再次遍历            
	}

}
//把输出的功能，写到一个类的方法中，然后调用该方法即可
class MyTools{
	//方法，接受一个二维数组
	public void printArr(int[][] map) {
		System.out.println("==============");
		//对传入的map数组进行遍历输出
		for(int i=0;i<map.length;i++) {
			for(int j=0;j<map[i].length;j++) {
				System.out.print(map[i][j]+"\t ");
			}
			System.out.println();
		}
	}
}
//方法的好处：1.提高了代码的复用性
//成员方法的定义
//public返回数据类型 方法名（形参列表..）{ //方法体
//        语句
//        return 返回值；}
/*1.参数列表：表示成员方法输入 cal（int n）
  2.数据类型（返回类型）：表示成员方法输出，void表示没有返回值
  3.方法主题：表示为了实现某一功能的代码
  4.return语句不是必须的
 */
//访问修饰符有public protected 默认 private
 

```

## MethodDetail01

```java
package day04;

public class MethodDetail01{

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//1.一个方法最多有一个返回值【思考，如何返回多个结果 返回数组】
			AA a=new AA();
			int res[]=a.getSumAndSub(1, 4);
			System.out.println("和="+res[0]);
			System.out.println("差="+res[1]);
			
			
			//细节：调用带参数的方法时，一定对应着参数列表传入相同类型或兼容类型 的参数
	        byte b1 =1;
	        byte b2=2;
			a.getSumAndSub(b1,b2);//byte->int
		//	a.getSumAndSub(1.1,1.8);// double ->int(x)
			//细节：实参和形参的类型要一致或兼容、个数、顺序必须一致
	    //  a.getgetSumAndSub(100);//个数不一致×
			//细节：方法不能嵌套定义
	}
}
class AA{
	public int[] getSumAndSub(int n1,int n2) {
		int[] resArr =new int[2];
		resArr[0]=n1+n2;
		resArr[1]=n1-n2;
		return resArr;
		
	}
	//2.返回类型可以为任意类型，包含基本数据类型或应用类型（数组，对象）
	// 看getSumAndSub
	//3.如果方法要求有返回数据类型，则方法中最后的执行语句必须为 return值
	//而且要求返回值类型必须和return的值类型一致或兼容
	//如果方法是void，则方法体中可以没有return语句，或者 只写return
	
  
    


}


```

## MethodDetail02

```java
package day04;

public class MethodDetail02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		A a=new A();
		a.sayOK();
		a.m1();

	}

}
class A{
	//同一个类中的方法调用：直接调用即可
	//
	public void print(int n) {
		System.out.println("print（）的方法调用n="+n);
	}
	public void sayOK() {//sayOK调用 print（直接调用即可）
		print(10);
		System.out.println("继续执行sayOK（）");}
	
		//跨类中的方法A类调用B类方法：需要通过对象名调用
		
		public void m1(){
			//创建B对象，然后再调用方法即可
			System.out.println("m1()方法被调用");
			B b=new B();
			b.hi();
			System.out.println("m1()继续执行");
		}
	}	

class B{
	public void hi(){
		System.out.println("B类中的hi（）被执行");
		
	}
}

```

## MethodExercise01

```java
package day04;

import java.util.Scanner;

public class MethodExercise01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		AAA a=new AAA();
//		int n;
//		Scanner c=new Scanner(System.in);
//		n =c.nextInt();
//		boolean b=a.isOdd(n);
//		if(b=false) {
//		System.out.println("是偶数");}
//		else {
//         System.out.println("是奇数");
//	}
		//使用print方法
		Scanner c=new Scanner(System.in);
		int x1=c.nextInt();
		int x2=c.nextInt();
		char q=c.next().charAt(0);	
		a.print(x1, x2, q);
	}
}
//编写类AAA，有一个方法：判断一个数是奇数odd还是偶数，返回booolean
class AAA{
	//思路
	//1.方法的返回类型boolean
	//2.方法的名字  isOdd
	//3.方法的形参 （int number)
	//4.方法体,判断
	public boolean isOdd(int num) {
//	if(num%2!=0) {
//		return ture;	
//	}else {
//		return false;
//	}
	//return num%2!=0?true:false;
		return num%2!=0;
	}	
	//根据行、列、字符打印 对应行数和列数的字符，
	//比如：行：4，列：4，字符#，咋打印相应的效果
	/*
	 * ####
	 * ####
	 * ####
	 * ####
	 * 
	 */
	//1.方法的返回类型 void
	//2.方法的名字 printchar
	//3.方法的形参(int row，int column，char c)
	//4.方法体，循环
	public void print(int row,int col,char c) {
		for(int i=0;i<row;i++) {
			for(int j=0;j<col;j++) {//输出每一行
				System.out.print(c);
			}
			System.out.println();//换行
		}
	}
}

```

## MethodExercise02

```java
package day04;

public class MethodExercise02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//编写一个方法copyPerson，可以复制一个Person对象，返回复制的对象。克隆对象，
   //注意要求得到新对象和原来的对象是两个独立的对象，，只是他们的属性相同
	Person03 p=new Person03();
	  p.name="milan";
	  p.age=100;
	 MyTools02 tools= new MyTools02();
	Person03 p2=tools.copyPerson(p);
	//到此p和p2是Person对象，但是是两个独立的对象，属性相同
	System.out.println("p的属性age"+p.age+",p的名字"+p.name);
	System.out.println("p2的属性age"+p2.age+",p的名字"+p2.name);
	//这里老师提示：可以通过输出对象的hashCode看看对象是否是一个
	System.out.println(p==p2);
	}

}
class Person03{
	String name;
	int age;
}
class MyTools02{
	//编写一个方法copyPerson，可以复制一个Person对象，返回复制的对象。克隆对象，
    //注意要求得到新对象和原来的对象是两个独立的对象，，只是他们的属性相同
	//1.方法的返回类型boolean
		//2.方法的名字  isOdd
		//3.方法的形参 （int number)
		//4.方法体,判断
	public Person03 copyPerson(Person03 p) {
		//创建一个新的对象
	Person03 p2=new Person03();
	p2.name=p.name; //把原来的名字赋给p2.name
	p2.age=p.age;//把原来对象的年龄赋给p2.age
	return p2;
	}
}
```

## MethodParameter01

```java
package day04;

import java.util.Scanner;

public class MethodParameter01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
    Abc obj=new Abc();
    Scanner input =new Scanner(System.in);
    int n1=input.nextInt();
    int n2=input.nextInt();
    
    obj.swap(n1, n2);
	}

}
class Abc{
	public void swap(int a,int b) {
		System.out.println("\na和b交换前的值a="+a+"\tb="+b);
		//完成a和b的交换
		int tmp=a;
		a=b;
		b=tmp;
		System.out.println("\na和b交换后的值a="+a+"\tb="+b);
	}


	
}
```



## MethodParameter02

```java
package day04;

public class MethodParameter02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//测试
		AB b=new AB();
//		int arr[]= {1,2,3};
//		b.test100(arr);//调用方法
//		System.out.println("main的arr数组");
//		//遍历数组
//		for(int i=0;i<arr.length;i++) {
//			System.out.println(arr[i]+"\t");
//		}
//    System.out.println();
    //测试
    Person02 p=new Person02();
    p.name="jack";
    p.age=10;
    
    b.test200(p);
    //测试题，如果test200执行的是p=null，下面结果为10
    //测试题，如果test200执行的是p=new Person（）;下面结果为10
    System.out.println("main的p.age"+p.age);
	}

}
class 	Person02{
	String name;
	int age;
	
}
class AB{
	public void test200(Person02 p) {
		//p.age=10000;//修改对象属性
		//p=null;
		p=new Person02();
		p.name="Tom";
		p.age=99;
	}	
	
	//B类中编写一个方法test100
	//可以接受一个数组，在方法中修改该数组，看看原来的数组是否发生变化
	
	public void test100(int arr[]) {
		arr[0]=200;//修改元素
		//遍历数组
		System.out.println("test100d的arr数组");
		for(int i=0;i<arr.length;i++) {
			System.out.println(arr[i]+"\t");
		}
		System.out.println();
	}
}
```

## OverLoad

```java
package day04;

public class OverLoad {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
     MyCalculator mc=new MyCalculator();
     System.out.println(mc.calculate(1, 2));
     System.out.println(mc.calculate(1.1, 2));
	}

}
class MyCalculator{
	//下面的四个calculate方法构成了重载
	//两个整数的和
	public int calculate(int n1,int n2){
		return n1+n2;
		
	}
	//一个整数，一个double的和
	public double calculate(int n1,double n2){
		return n1+n2;
		
	}//一个double，一个int的和
	public double calculate(double n2,int n1){
		System.out.println("calculate(double n1，int n2)被调用");
		return n1+n2;
	}//三个int的和
	public int calculate(int n1,int n2,int n3){
		return n1+n2+n3;
		
	}
}
```



 