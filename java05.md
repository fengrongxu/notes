# java05

## Recursion01

```java
package day05;

public class Recursion01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
    T  t1=new T();
    t1.test(4);//输出n=2 n=n3 n=4
 int res=   t1.factorial(5);
 System.out.println("5的阶乘的结果="+res);
	}

}
class T{
	//分析
	public void test(int n) {
		if(n>2) {
			test(n-1);
		}
		System.out.println("n="+n);
		}
	//factorial阶乘
	public int factorial(int n) {
		if(n==1) {
			return 1;
		}else {
			return factorial(n-1)*n;
		}
	}
	}
//1.执行一个方法时，就创建一个新的受保护的独立空间（栈空间）
//2.方法的局部变量是独立的，不会相互影响，比如n变量
//3.如果方法中使用的是引用数据变量（比如数组，对象），就会共享该引用类型的数据
//4.递归必须向退出递归的条件逼近，否则就是无限递归，出现StrackOverflowError,死鬼了；）
//5.当一个方法执行完毕时，同时当方法执行完毕或者返回时，该方法也执行完毕。

```

## RecursionExercise01

```java
package day05;

import java.util.Scanner;

public class RecursionExercise01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println("请输入一个整数");
    TT t1=new TT();
    Scanner input=new Scanner(System.in);
   // long n=input.nextInt();
   // System.out.println("当n="+n+"时对应的斐波那契数是"+t1.fibonacci(n));
    int day;
    day=input.nextInt();
    System.out.println("第"+day+"天有"+t1.peach(day)+"个桃子");
	}

}
class TT{
	/*
	 请使用递归的方式求出斐波那契数1,1,2,3,5,8,13...给你一个整数n 
	 思路分析
	 1.当n=1时，斐波那契数是1
	 2.当n=2时，斐波那契数是1
	 3.当n>=3 斐波那契数 是前两个数的和
	 4.这里就是一个递归的思路
	 */
	public int fibonacci(long n) {
		if(n>=1){
		if(n==1||n==2) {
			return 1;
		}else {	
			return fibonacci(n-1)+fibonacci(n-2);
		}
	    }else{
			System.out.println("要求输入的n>=1的整数");
		}
		return -1;
		
	}

    /*
       猴子吃桃子问题：有一堆桃子，猴子第一天吃了其中的一半，并再多吃了一个！
       以后每天猴子都吃其中的一半，然后再多吃一个。当到第10天时，
       想再吃时（即还没吃），发现只有一个桃子了。问题：最初共有多少个桃子
     
        思路分析 逆推
        1.day=10 时有1个桃子
        2.day=9  时有（day10+1）*2=4
        3.day=8  时有（day9+1）*2=10
        4.规律就是  前一天的桃子 =（后一天的桃子 +1）*2
        5.递归
        */
        public int peach(int day) {
        	if(day==10) { //第10天，只有一个桃
        		return 1;
        	}else if(day>=1&&day<=9){
        		return(peach(day+1)+1)*2;	
        	}else {
        		System.out.println("day在1-10，请重新输入");
        		return -1;
        	}
        	
        }
        }
```

## HanoiTower

```java
package day05;

import java.util.Scanner;

public class HanoiTower {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Tower tower=new Tower();
		System.out.println("请输入汉诺塔上面要移动的盘子数");
		Scanner n1=new Scanner(System.in);
         int n=n1.nextInt();
		tower.move(n,'A','B','C');

	}

}
class Tower{
	//方法
	//num表示要移动的个数，a，b，c分别表示A塔，B塔，C塔
	public void move(int num,char a,char b,char c) {
		//如果只有一个盘num=1
		if(num==1) {
			System.out.println(a+"->"+c);
		}else {
			//如果有多个盘，可以看成两个，最下面的和上面的所有盘（num-1）
			//（1）先移动上面的所有盘到b，借助c
			move(num-1,a,c,b);
			//(2)把最下面的这个盘，移动到c
			System.out.println(a+"->"+c);
			//(3)再把b的所有盘，移动到c，借助a
			move(num-1,b,a,c);
			
		}
		
	}
}

```

