# java06

## OverLoadExercise

```java
package day04;

public class OverLoadExercise {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Methods method=new Methods();
         method.m(10);//100
         method.m(10,20);//200
         method.m("ok");//ok
       System.out.println( method.max(1.0, 2.0, 3.0));
	}
}
/* 
 编写程序，类Methods中定义三个重载方法并调用。方法名为m。三个方法分别接受一个int型
 、两个int型，相乘并输出结果，输出字符串信息，在主类的main（）方法中
 分别用参数区别调用三个方法
 */
/*
 定义三个重载方法max(),第一个方法，返回两个int值中的最大值，
 第二个方法，返回两个double值中的最大值，第三个方法
 返回三个double值中的最大值，并分别调用三个方法
 */
class Methods{
	//分析
	//1方法名max
	//2形参(int,int)
	//3.int
	public int max(int n1,int n2) {
		return n1>n2?n1:n2;
	}
	public double max(double n1,double n2) {
		return n1>n2?n1:n2;
	}
	public double max(double n1,double n2,double n3) {
		return (n1>n2?n1:n2)>n3?(n1>n2?n1:n2):n3;
	} 
	//不使用自动转换比 使用自动转换 优先级高
	
	
	
	//分析 
	//1方法名m
	//2形参int
	//3void
	public void m(int n) {
		System.out.println("平方="+(n*n));  
	}
	//1方法名m
		//2形参(int,int)
		//3void
	public void m(int n1,int n2) {
		System.out.println("相乘="+(n1*n2));
	}
	//1方法名m
			//2形参(String)
			//3void
	public void m(String str) {
		System.out.println("传入的str="+str);
	}
}

```

## VarParameter01

```java
package day06;

public class VarParameter01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
            HspMethod m=new HspMethod();
           System.out.println(m.sum(1,5,100));//106
           System.out.println(m.sum(1,19));//20
	}

}
class HspMethod{
	//可以计算 2个数的和，3个数的和，4,5，..
	//可以使用方法重载
//	public int sum(int n1,int n2) {//2个数的和
//		return n1+n2;
//	}
//	public int sum(int n1,int n2,int n3) {//3个数的和
//		return n1+n2+n3;
//	}
//	public int sum(int n1,int n2,int n3,int n4) {//4个数的和
//		return n1+n2+n3+n4;
	//.....
	//上面的三个方法名称相同，功能相同，参数个数不同-> 使用可变参数优化
	//1.int..表示接受的是可变参数，类型是int，既可以接受多个int（0-多）
	//2.使用可变参数时
	//3.遍历nums 求和即可
	//}
	public int sum(int...nums) {
	//	System.out.println("接受的参数个数="+nums.length);
		int res=0;
		for(int i=0;i<nums.length;i++) {
			res+=nums[i];
		}
		return res;
	}
}












//java允许将同一个类中多个同名同功能单参数个数不同的方法，封装成一个方法
//就额可以通过可变参数实现
//基本语法
//访问修饰符 返回类型 方法名（数据类型 ..形参名）{
//}

```

## VarParameterDetail

```java
package day06;

public class VarParameterDetail {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//细节：可变参数的实参可以为数组
		int arr[]= {1,2,3};
		T t1=new T();
		t1.f1(arr);

	}

}
class T{
	public void  f1(int...nums) {
		System.out.println("长度="+nums.length);
		
	}
	//细节：可变参数可以和普通类型的参数一起放在形参列表，但必须保证可变参数在最
	//后
	public void f2(String d1,double...nums) {
		
	}
}
//1可变参数的实参可以为0个或任意多个
//2可变参数的实参可以为数组
//3可变参数本质就是数组
//4可变参数可以和普通类型的参数一起放在形参列表，但必须保证可变参数在最后
//5一个形参列表只能出现一个可变参数
```

## VarParameterExercise

```java
package day06;

public class VarParameterExercise {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        
		HspMethod01 hm=new HspMethod01();
		System.out.println(hm.showScore("milan", 90,80.0));
		System.out.println(hm.showScore("terry", 2.0,5,6,85,65));
	}

}
class HspMethod01{
	/*有三个方法，分别实现返回姓名和两门课程（总分）
	 * 返回姓名和三门课成绩（总分），返回姓名和五门课成绩（总分），
	 * 封装成一个可变参数的方法
	 */
	//分析1.方法名 showScore 2.形参(String,double...)3.返回String
	public String showScore(String name,double...scores) {
		double totalScore=0;
		for(int i=0;i<scores.length;i++) {
			totalScore +=scores[i];
		}
		return name+"有"+scores.length+"门科的成绩总分为"+totalScore;
	}
	
}

```

## VarScope01

```java
package day06;

public class VarScope01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}

}
//1在java编程中，主要的变量就是属性
//2除了属性之外的其他变量，作用域为定义它的代码块中
//3全部变量（属性）可以不赋值，直接使用，因为有默认值，
//局部变量必须在赋值后，才能使用，因为没有默认值
//
class Cat{
	//全局变量：也就是属性，作用域为整个类体Cat类：cry eat 等方法的属性
	//属性在定义时，可以直接赋值
	
	int age =10;//指定的值是10
	double weight;//不赋值默认值是0.0
	{
		int num=100;//不是属性，在代码块里定义
	}
	public void hi() {
		//局部变量必须赋值才能使用，因为没有默认值
		//int num;×
		int num=1;
		String address ="北京的猫";
		System.out.println("address"+address);
		System.out.println("num="+num);
		System.out.println("weight"+weight);
	}
	public void cry() {
		
		//1.局部变量一般是指在成员方法中定义的变量
		//2.n和name都是局部变量
		//3.n和name的作用域在cry方法中
		int n=10;
		String name ="jack";
		
	}
	public void eat() {
		System.out.println("在eat方法中使用age="+age);
		//System.out.println("在eat方法中使用cry的变量"+name);不允许使用
	}
}
```

## VarScopeDetail

```java
package day06;

public class VarScopeDetail {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Person p1=new Person();
		/*
		3.细节 属性生命周期较长，伴随着对象的创建而创建，伴随着对象的销毁而销毁
		 局部变量，生命周期较短，伴随着它的代码块的执行而创建
		 伴随着代码块的结束而销毁。即在一次方法调用过程中
		 */
		p1.say();//当执行say方法时，say方法的局部变量比如name，会创建，
		//当say执行完毕后，	
		//name局部变量被销毁，但是属性（全局变量）仍然可以使用
             T1 t1=new T1();
             t1.test();//第一种 跨类访问对象属性的方式
             t1.test2(p1);//第二种 跨类访问对象属性的方式
	}

}
class T1 {
	//4细节 全局变量（属性）：可以被本类使用，或其他类使用（通过对象调用）
	public void test() {
		Person p1=new Person();
		System.out.println(p1.name);//jack
	}
	public void test2(Person P) {
		System.out.println(P.name);//jack
	}
}
class Person{
	//5细节 属性可以在前面加修饰符(public,protected,private..)，局部不能加
	public int age=20;
	String name ="jack";
	public void say() {
		//1细节 属性和局部变量可以重名，访问时遵循就近原则
		//public String name="King"; × 不允许加修饰符
		String name="King";
		System.out.println("say()name="+name);//输出King
	}
	public void hi() {
		String address="北京";
		//String address="上海";×2细节 在一个方法中局部变量不能重名
		String name="frx";//ok的，在不同的作用域里面
	}
}
```

