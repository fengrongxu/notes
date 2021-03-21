# java

## ArrayAdd01

```java
package day02;

public class ArrayAdd01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		/*要求：实现动态的给数组添加元素效果，实现对数组扩容。ArrayAdd.java
		 1.原始数组使用静态分配 int arr[]={1,2,3}
		 2.增加的元素4，直接放在数组的最后arr={1,2,3,4}
		 3.用户可以通过如下方法来决定是否继续添加，添加成功，是否继续？y/n
		 思路分析
		 1.定义初始数组 int arr[]={1,2,3}
		 2.定义一个新数组int arrNew[]=new int[arr.length+1]; 
		 3.遍历arr数组，依次将arr的元素拷贝到arrNew数组
		 4.将4赋给 arrNew[arr.length-1]=4;把4赋给arrNew最后一个元素
		 5.让arr指向arrNew； arr=arrNew；那么原来的arr数组就被销毁		 */
		int arr[]= {1,2,3};
		int arrNew[]=new int[arr.length+1];
		for(int i=0;i<arr.length;i++) {
			arrNew[i]=arr[i];
		}
         //把4赋给arrNew最后一个元素
		arrNew[arrNew.length-1]=4;
		//让arr指向arrNew，
		arr=arrNew;
		//输出arr 看看效果
		System.out.println("=====arr扩容后元素情况========");
		  for(int i=0;i<arr.length;i++) {
	       arrNew[i] =arr[i];
	       System.out.print(arr[i]+"\t");
		  }  	
	}

}

```

## ArrayAdd02

```java
package day02;

import java.util.Scanner;

public class ArrayAdd02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		/*要求：实现动态的给数组添加元素效果，实现对数组扩容。ArrayAdd.java
		 1.原始数组使用静态分配 int arr[]={1,2,3}
		 2.增加的元素4，直接放在数组的最后arr={1,2,3,4}
		 3.用户可以通过如下方法来决定是否继续添加，添加成功，是否继续？y/n
		 思路分析
		 1.定义初始数组 int arr[]={1,2,3}
		 2.定义一个新数组int arrNew[]=new int[arr.length+1]; 
		 3.遍历arr数组，依次将arr的元素拷贝到arrNew数组
		 4.将4赋给 arrNew[arr.length-1]=4;把4赋给arrNew最后一个元素
		 5.让arr指向arrNew； arr=arrNew；那么原来的arr数组就被销毁
		 6.创建一个Scanner可以接收用户输入
		 7.因为用户什么时候退出，不确定，老师使用do-while+break控制	
		 	 */
		Scanner myScanner=new Scanner(System.in);
		
		
		int arr[]= {1,2,3};
		do {
		int arrNew[]=new int[arr.length+1];
		for(int i=0;i<arr.length;i++) {
			arrNew[i]=arr[i];
		}
		System.out.println("请输入你要添加的元素");
		int addNum=myScanner.nextInt();
         //把addNum赋给arrNew最后一个元素
		arrNew[arrNew.length-1]=addNum;
		//让arr指向arrNew，
		arr=arrNew;
		//输出arr 看看效果
		System.out.println("=====arr扩容后元素情况=====");
		  for(int i=0;i<arr.length;i++) {
	       arrNew[i] =arr[i];
	       System.out.print(arr[i]+"\t");
		  }  
		  //问用户是否继续
		  System.out.println("是否继续添加y/n");
		  char key=myScanner.next().charAt(0);
		  if(key=='n') {//如果输入n，就结束
			  break;
		  }
		}while(true);
		System.out.println("你已退出了添加");
	}

}
```

## ArrayAssign

```java
package day02;

public class ArrayAssign {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//基本数据类型赋值，赋值方式为值拷贝
		//n2的变化，不会影响到n1的值
		int n1=10;
		int n2=n1;
		n2=80;
		System.out.println("n1="+n1);
		System.out.println("n2="+n2);
		//数组在默认情况下是引用传递，赋的值是地址，赋值方式为引用传达
		//是一个地址，arr2变化会影响到arr1
		int arr1[]= {1,2,3};
		int arr2[]=arr1;//把arr1赋给arr2
        arr2[0]=10;
        //看看arr1的值
        System.out.println("=======arr1的元素========");
        for(int i=0;i<arr1.length;i++) {
        	System.out.println(arr1[i]);
        	
        }
	}

}

```

## ArrayCopy

```java
package day02;

public class ArrayCopy {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        //将int arr1[]={10,20,30};拷贝到arr2数组，要求数据空间是独立的
	 int arr1[]= {10,20,30};
	    //创建一个新的数组arr2，开辟新的数据空间
	    //大小 arr.length；
	    //
	     int arr2[]=new int[arr1.length];
	     //遍历arr1，把每个元素拷贝到对应的位置
	     for(int i=0;i<arr1.length;i++) {
	    	 arr2[i]=arr1[i];
	     }
	     //修改arr2
	     arr2[0]=100;
	     //输出arr1
	     System.out.println("=======arr1的元素========");
	        for(int i=0;i<arr2.length;i++) {
	        	System.out.println(arr2[i]);//100,20,30
	        	
	        } 
	}

}

```

## ArrayExercise01

```java
package day02;

public class ArrayExercise01 {

	private static int i;

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		/*
		  创建一个char类型的26个元素的数组，分别放置‘A’-‘Z’
		  使用for循环访问所有元素并打印出来
		  提示：char类型数据运算‘A’+1-》‘B’
		  思路分析
		  1.定义一个 数组 char[] chars=new char[26];
		  2.因为‘A‘+1='B'类推，所以用for来赋值
		  3.使用for循环访问所有元素并打印出来
		 */
          char[] chars =new char[26];
          for(int i=0;i<chars.length;i++) {//循环26次
        	  //chars[] 是char[]
        	  //chars[i]是char
        	  chars[i]=(char) ('A'+i);  //'A'=i是int，需强制转换  
          System.out.println(chars[i]+" ");
          
	}
	}
}

```

## ArrayExercise02

```java
package day02;

public class ArrayExercise02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        //求出一个数组int[]的最大值{4,-1,9,10,23},并得到对应的下标
		//思路分析
		//1.定义一个int数组int[]arr ={4,-1,9,10,23}
		//2.假定max=arr[0]是最大值，maxIndex=0；
		//3.从下标1开始遍历arr，如果max<当前元素，说明max不是真正的最大值，
		//把当前的元素赋给max；maxIndex=当前元素下表
	    //4.当我们遍历真个数组arr后，max就是真正的最大值，maxIndex就是最大值下标
	    int[]arr= {4,-1,9,10,23};
	    int max=arr[0];//假定第一个元素就是最大值
	    int maxIndex =0;//
	    for(int i=1;i<arr.length;i++) {
	    	if(max<arr[i]) { //如果max小于当前元素
	    		max =arr[i];//把当前元素赋给max
	    		maxIndex=i;
	    	}
	    }
	
	System.out.println("max="+max+"  maxIndex"+maxIndex);
	
}

}

```

## ArrayReverse01

```java
package day02;

public class ArrayReverse01 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        //定义数组
		int arr[]= {11,22,33,44,55,66};
		//1.把arr[0]和arr[5]进行交换{66,22，33,44,55,11}
		//2.把arr[1]和arr[4]进行交换{66,55，33,44,22,11}
		//3.把arr[2]和arr[3]进行交换{66,55，44,33,22,11}
		//4.一共要交换3次 =arr.length/2
		//5.每次交换时，对应的下标是arr[i]和arr[arr.length-1-i]
		//代码
		//优化
		int temp=0;
		int len=arr.length;
		for(int i=0;i<len/2;i++) {
			temp=arr[len-1-i];//保存
			arr[len-1-i]=arr[i];
			arr[i]=temp;
		
		}
		 System.out.println("=======翻转后的数组========");
	        for(int i=0;i<arr.length;i++) {
		System.out.print(arr[i]+"\t");
		}
		
	}

}

```

## ArrayReverse02

```java
package day02;

public class ArrayReverse02 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        //定义数组
		int arr[]= {11,22,33,44,55,66};
//		使用逆序赋值方式
		//1.先创建一个新数组arr2，大小arr.length
		//2.逆序遍历arr，将每个元素拷贝到arr2的元素中（顺序拷贝）
		//3.建议增加一个循环变量j->0->5
		int arr2[]=new int[arr.length];
		for(int i=arr.length-1,j=0;i>=0;i--,j++) {//逆序遍历arr
			arr2[j]=arr[i];
			//4.当for循环结束，arr2就是一个逆序的数组
			//5.让arr指向arr2数据空间,此时arr原来的数据空间没有变量引用
			//会被当做垃圾注销
		}	arr=arr2;
			System.out.println("=======arr的元素情况=======");
			//6.输出arr看看
			for(int i1=0;i1<arr.length;i1++) {
				System.out.print(arr2[i1]+"\t");
			}
			
		}
		
		
	}



```

## BubbleSort

```java
package day02;

public class BubbleSort {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
       //化繁为简
		
		/*
		  数组[24,69,80,57,13]
		  第一轮排序：目标把最大数放在后面
		  第1次比较[24,69,80,57,13]
		  第2次比较[24,69,80,57,13]
		  第3次比较[24,69,57,80,13]
		  第4次比较[24,69,57,13,80]
		 
		 */
		int arr[]= {24,69,80,57,13};
		int temp=0;//用于辅助交换的变量
		//将多轮循环使用最外层循环包括起来即可
		for(int i=0;i<arr.length-1;i++) {//外层循环是4次
			for(int j=0;j<arr.length-1-i;j++) { //内层比较4-3-2-1
				//如果前面的数>后面的数，就交换
				if(arr[j]>arr[j+1]){
				temp=arr[j];
				arr[j]=arr[j+1];
				arr[j+1]=temp;//[400,10]			 
			}
		}
		
			System.out.println("==第"+i+"循环比较结果==");
			for(int j=0;j<arr.length;j++) {
				System.out.print(arr[j]+"\t");
				
			}
			System.out.println();
		}
		
//		System.out.println();
//		for(int j=0;j<4;j++) {//4次比较
//			//如果前面的数>后面的数，就交换
//			if(arr[j]>arr[j+1]){
//			temp=arr[j];
//			arr[j]=arr[j+1];
//			arr[j+1]=temp;//[400,10]			 
//		}
//	}
//		System.out.println("==第1轮==");
//		for(int j=0;j<arr.length;j++) {
//			System.out.print(arr[j]+"\t");
//		}
//		/*
//		 第2轮排序：目标把第二大数放在倒数第二位置
//		 第1次比较[24,69,57,13,80]
//		 第2次比较[24,57,69,13,80]
//		 第3次比较[24,57,13,69,80]
//		 */
//		System.out.println();
//		for(int j=0;j<3;j++) {//3次比较
//			//如果前面的数>后面的数，就交换
//			if(arr[j]>arr[j+1]){
//			temp=arr[j];
//			arr[j]=arr[j+1];
//			arr[j+1]=temp;			 
//		}
//	}
//		System.out.println("==第2轮==");
//		for(int j=0;j<arr.length;j++) {
//			System.out.print(arr[j]+"\t");
//		}
//		/*
//		 第3轮排序：目标把第3大数放在倒数第三的位置
//		 第1次比较[24,57,13,69,80]
//		 第2次比较[24,13,57,69,80]
//		 */
//		
//		
//		System.out.println();
//		for(int j=0;j<2;j++) {//2次比较
//			//如果前面的数>后面的数，就交换
//			if(arr[j]>arr[j+1]){
//			temp=arr[j];
//			arr[j]=arr[j+1];
//			arr[j+1]=temp;			 
//		}
//	}
//		System.out.println("==第3轮==");
//		for(int j=0;j<arr.length;j++) {
//			System.out.print(arr[j]+"\t");
//		}
//		System.out.println();
//		for(int j=0;j<1;j++) {//1次比较
//			//如果前面的数>后面的数，就交换
//			if(arr[j]>arr[j+1]){
//			temp=arr[j];
//			arr[j]=arr[j+1];
//			arr[j+1]=temp;			 
//		}
//	}
//		System.out.println("==第4轮==");
//		for(int j=0;j<arr.length;j++) {
//			System.out.print(arr[j]+"\t");	
//		}
//				 
		
		
	}	

}

```

## TwoDimeensionalArray01

```java
package day02;

public class TwoDimeensionalArray01 {
	//编写一个main方法
	public static void main(String[] args){
		/*
		 请用二维数组输出如下图形
		  0 0 0 0 0 0
		  0 0 1 0 0 0
		  0 2 0 3 0 0
		  0 0 0 0 0 0
		 */
		//什么是二维数组；
		//老韩解读
		//1.从定义形式上看 int[][]
        //2.可以这样理解，原来的一维数组的每个元素是一维数组，就会构成二维数组
		int[][] arr= {{0,0,0,0,0,0},
				      {0,0,1,0,0,0},
				      {0,2,0,3,0,0},
				      {0,0,0,0,0,0}};
		//关于二维数组的关键概念
		//(1)
		System.out.println("二维数组的元素个数=" + arr.length);
		//(2)二维数组的每个元素是一维数组，所以如果需要得到每个一维数组的值
		//  还需要再次遍历
		//（3）如果我们要访问第（i+1)个一维数组的第j+1个值 arr[i][j];
		//   举例访问3，=》他是第3个一维数组的的第4个值  arr[2][3]
		System.out.println("第3个一维数组的的第4个值"+arr[2][3]);
		
		
		//输出二维图形
		for(int i=0;i<arr.length;i++) {//遍历二维数组的每个元素
		    //遍历二维数组的每个元素（数组）
			//老韩解读
			//1.arr[i]表示 二维数组的第i+1个元素
			//2.arr[i].length 得到对应的每一个数组的长度
			for(int j =0;j<arr[i].length;j++) {
				System.out.print(arr[i][j]+" ");//输出一维数组
		}
			System.out.println();//换行
		}
				}

}

```

## TwoDimeensionalArray02

```java
package day02;

public class TwoDimeensionalArray02 {
	//编写一个main方法
	public static void main(String[] args) {
	//	int arr[][]=new int[2][3];
		int arr[][];//声明二维数组
		arr=new int[2][3];//再开空间
		arr[1][1]=8;
		//遍历arr数组
		for(int i=0;i<arr.length;i++) {
			for(int j=0;j<arr[i].length;j++) {
				System.out.print(arr[i][j]+" ");
			}
			System.out.println();//换行
		}
	}

}
  
```

## TwoDimeensionalArray03

```java
package day02;

public class TwoDimeensionalArray03 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		/*看一个需求：动态创建下面二维数组，并输出
		  i=0:1
		  i=1:2 2
		  i=2:3 3 3
		  一个有三个一维数组，每个一维数组的元素是不一样的
		 
		 */
		int[][]arr=new int[3][];//
		for(int i=0;i<arr.length;i++) {//遍历arr每一个一维数组
			//给每一个一维数组开空间 new
			//如果没有给一维数组 new，那么arr[i]就是null
			arr[i]=new int[i+1];
			//遍历一维数组，并给一维数组的每个元素赋值
			for(int j=0;j<arr[i].length;j++) {
				arr[i][j]=i+1;//赋值
			}
			
		}
		System.out.println("=======arr元素====");
        //遍历arr输出
		for(int i=0;i<arr.length;i++){
			//输出arr的每个一维数组
			for(int j=0;j<arr[i].length;j++) {
				System.out.print(arr[i][j]+" ");
			}
			
			System.out.println();//换行
		
		}
	}

}

```

## TwoDimeensionalArray04

```java
package day02;

public class TwoDimeensionalArray04 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		/*
		 * int arr[][]={{4,6},{1,4,5,7},{-2}};遍历该二维数组，并得到和
		 思路
		 1.遍历二维数组，并将各个值累计到 int sum
		 
		 */
		int arr[][]={{4,6},{1,4,5,7},{-2}};
		int sum=0;
         for(int i=0;i<arr.length;i++) {
        	 //遍历每个一维数组
        	 for(int j=0;j<arr[i].length;j++) {
        		 sum+=arr[i][j];
        	 }
         }
         System.out.println("sum="+sum);
	}

}

```

