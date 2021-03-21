# java



## circle

```java
package day01;

import java.util.Scanner;

public class circle01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//Scanner input =new Scanner(System.in);
		//int i=1;
//		while(i<=n) {//while是先判断 在执行语句 而 do..while是先进行一次循环，在判断条件
//			System.out.println("i="+i);
//			i++;
//		}
//		do{
//			System.out.println("i="+i);
//			i++;
//		}while(i<=n); {
//			
//		}
//		for(i=1;i<=n;i++) {
//			System.out.println("i="+i);
//			
//		}
//        for(int i=0;i<n;i++) {
//        	for(int j=0;j<n;j++) {
//        		System.out.print("*");
//        	}
//        	System.out.println();
//        }
//		int nums[]= {1,2,3,4,5,6};//定义一个数组
//		for(int num:nums) {
//			System.out.println("num="+num);
//		}
		for(int i=1;i<=10;i++) {
			if(i==2)
			System.out.println("i="+i);
		}
	}

	}

```

```

```

## For each

```java
package day01;
public class Foreach{
public static void main(String[] args) {
   int [][]nums= {{1,2,3},{4,5,6},{7,8,9}};
   for(int []arr:nums) {
	   for(int num:arr) {
		   System.out.println(num);
	   }
	   
   }
}
}
```



##  ++

```java
package day01;

public class HelloWorld {
	public static void main(String[] args) {
		int a=2;
		char c='\n';
	System.out.println(a++);
	System.out.println(a);
	System.out.println(c);
	System.out.println(++a);
	}
}

```



## select01

```java
 package day01;

import java.util.Scanner;

public class Select01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input =new Scanner(System.in);//导包的快捷键ctrl+shift+o(字母哦）
        System.out.println("请输入一个整数：");
      /*  int n =input.nextInt();
        if(n%2==0) {
        	System.out.println(n+"是偶数");
        }else {
        	System.out.println(n+"是奇数");
        }*/
//        int score =input.nextInt();
//	    if(score>=90) {
//	    	System.out.println("优秀");
//	    	
//	    }else if(score>=80) {
//	    	System.out.println("良好");
//	    }else if(score>=70) {
//	    	System.out.println("中等");
//	    }else if(score>=60) {
//	    	System.out.println("及格");
//	    }else {
//	    	System.out.println("不及格");
//	    }
        int score =input.nextInt();
	    int n=score/10;
	    switch(n) {
	    case 10:
	    	System.out.println("满分");
	    case 9:
	    	System.out.println("优秀");
	    case 8:
	        System.out.println("良好");
	    case 7:
	    	System.out.println("中等");
	    case 6:
	    	System.out.println("及格");
	    	break;
	    	default:
	    	System.out.println("不及格");
	    	break;
	    	
	    	
	    
	    }
	
	
	}
        
        

}

```

## Studytask01



```java
package day01;

public class Studytask01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int a=1;
		for(a=1;a<=100;a++) {
			if(a%3==0)
			
			System.out.println(a);
				
			}
			
		}

	

}
```

## Studytask02

```java
package day01;

import java.util.Scanner;

public class Studytask02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println("请输入1-12随机一个整数");
		Scanner a =new Scanner(System.in);
		int i=a.nextInt();
//               if(i>=3&&i<=5) {
//   		    System.out.println("春季");		}
//			else if(i>=6&&i<=8) {
//				System.out.println("夏季");
//				}
//				else if(i>=9&&i<=11) {
//					System.out.println("秋季");
//				}
//				else {
//					System.out.println("冬季");
//						
//					}
				switch(i) {
				case 3:
				case 4:
				case 5:
					System.out.println("春季");
					break;
				case 6:
				case 7:
				case 8:
					System.out.println("夏季");
					break;
				case 9:
				case 10:
				case 11:	
					System.out.println("秋季");
					break;
				case 12:
				case 1:
				case 2:
					System.out.println("冬季");
					break;
					
				
				}
	
	
	}
			

}
	



```

## Studytask03

```java
package day01;

public class Studytask03 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int i=1;
		int j,s=0;
		for(i=1;i<=9;i++) {
			for(j=1;j<=i;j++) {
				System.out.print(i+"*"+j+"="+i*j+"\t");
			}
			System.out.println();
		}
		

	}

}

```

## Studytask04

```java
package day01;
import java.util.Scanner;


public class Studytask04 {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println("请输入几个学生成绩");
		int j;
		
			int s[]=new int[1000];
			for(j=0;j<=s.length;j++){
		Scanner input =new Scanner (System.in);
		s[j]=input.nextInt();
//		switch(s[j]/10){
//		case 0:
//		case 1:
//		case 2:
//		case 3:
//		case 4:
//		case 5:
//			System.out.println("不及格");
//			break;
//		case 6:
//			System.out.println("及格");
//			 break;
//		case 7:
//			System.out.println("中等");
//			break;
//		case 8:
//			System.out.println("良好");
//			break;
//		case 9:
//		case 10：
//			System.out.println("优秀");
//			break;
//			default:
//				System.out.println("输入错误");
//			
//			}
		
//		}
		
		if(s[j]<60){
			System.out.println("不及格");
		}
		else	if(s[j]>=60&&s[j]<70){
			System.out.println("及格");
			
			}
			else if(s[j]>=70&&s[j]<80){
			System.out.println("中等");
			}
			else if(s[j]>=80&&s[j]<90){
			System.out.println("良好");
			}
			else if(s[j]>=90&&s[j]<=100){
			System.out.println("优秀");
		}
		}
	
	}

}

```



## Studytask05

```java
package day01;
import java.util.Scanner;


public class Studytask05 {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println("请输入一个整数n");
		Scanner input=new Scanner(System.in);
		int n=input.nextInt();
		System.out.println("0到"+n+"所有的偶数为");
		for(int i=0;i<=n;i++){
			if(i%2==0){
				System.out.println(i);
				}
			}
			System.out.println("0到"+n+"所有的奇数为");
			for(int j=0;j<=n;j++){
				if(j%2!=0){
					System.out.println(j);
				}
			}
	
				
				
			
			
		}
		

	}


```





