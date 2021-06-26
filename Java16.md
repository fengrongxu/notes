# JAVA16

## Math类

### MathMethod

```java
package com.study.math_;

public class MathMethod {
    public static void main(String[] args) {
        //abs 绝对值
        int abs=Math.abs(-9);
        System.out.println(abs);
        //2.pow 求幂
        double pow=Math.pow(2,6);//2的6次方
        System.out.println(pow);
        //3.ceil 向上取整  返回>=该参数的最小整数
        double ceil=Math.ceil(2.54646);
        System.out.println(ceil);//2.0
        //4.floor 向下取整 返回<=改参数的最小整数
        double floor=Math.floor(4.0001);
        System.out.println(floor);//4.0
        //5.round 四舍五入
        long round=Math.round(5.5);
        System.out.println(round);//6.0
        //6.sqrt 开方
        double sqrt=Math.sqrt(4);
        System.out.println(sqrt);
        //7. random 求随机数
        //random 是返回 0<=x<1
        //返回一个 a<=x<=b
        //(int)(a)<=x<=(int)(a+Math.random()*(b-a+1))
        System.out.println((int)(0+(Math.random()*68)));
        int min=Math.min(6,9);
        int max=Math.max(1,90);
        System.out.println(min+" "+max);
    }

}

```

## Arrays类

### ArraySortCustom

```java
package com.study.arrays_;

import java.util.Arrays;
import java.util.Comparator;

public class ArraySortCustom {
    public static void main(String[] args) {
        int arr[]={1,-1,0,8,20};

      //  bubble01(arr);
        bubble02(arr, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                int i1=(Integer) o1;
                int i2=(Integer) o2;
                return i1-i2;//return i2-i1;
            }
        });
        System.out.println("=====排序后的情况======");
        System.out.println(Arrays.toString(arr));

    }
    //使用冒泡排序
    public static void bubble01(int []arr){
        int temp=0;
        for (int i = 0; i < arr.length-1; i++) {
            for (int j = 0; j < arr.length-i-1; j++) {
                //从小到大
                if(arr[j]>arr[j+1]){
                    temp=arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=temp;

                }

            }
        }
    }
    //结合冒泡+定制
    public static void bubble02(int []arr, Comparator c){
        int temp=0;
        for (int i = 0; i < arr.length-1; i++) {
            for (int j = 0; j < arr.length-i-1; j++) {
                //数组的排序由c.compare(arr[j],arr[j+1]) 决定
                if(c.compare(arr[j],arr[j+1])>0){
                    temp=arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=temp;

                }

            }
        }
    }
}

```

### ArrayMethod01

```java
package com.study.arrays_;

import java.lang.reflect.Array;
import java.util.Arrays;
import java.util.Comparator;

public class ArrayMethod01 {
    public static void main(String[] args) {
        Integer integer[] = {1, 10, 20};
//        for (int i = 0; i < integer.length; i++) {
//            System.out.println(integer[i]);
//        }
        //直接使用Arrays的toString方法 显示数组信息
        System.out.println(Arrays.toString(integer));

        Integer arr[] = {5, 2, -5, 56, 32, 0};
        Arrays.sort(arr);
        System.out.println("==排序后===");
        System.out.println(Arrays.toString(arr));
        //1.演示 sort方法 排序  默认从小到大 排序
        //2.因为数组是引用类型，所以通过sort排序后， 会直接影响到实参arr
        //3.sort重载的，也可以通过传入一个接口实现了 Comparator来实现定制排序
        //4.调用定制排序时，传入两个参数， （1）排序的数组arr
        //（2）实现了 Comparator接口的匿名内部类，要求实现compare 方法
        //5.
        //6.这体现了接口编程的方式，
        //  源码分析
        //（1）Arrays.sort(arr,new Comparator()
        // (2)最终到 private static <T> void binarySort(T[] a, int lo, int hi, int start,
        //                                       Comparator<? super T> c) （）
        //（3）执行到 binarySort方法的代码，会根据动态绑定机制 c.compare()执行我们传入的
        //  匿名内部类compare()
        // while (left < right) {
        //                int mid = (left + right) >>> 1;
        //                if (c.compare(pivot, a[mid]) < 0)
        //                    right = mid;
        //                else
        //                    left = mid + 1;
        //            }
        //（4）new Comparator<Object>() {
        //            @Override
        //            public int compare(Object o1, Object o2) {
        //                Integer i1 = (Integer) o1;
        //                Integer i2 = (Integer) o2;
        //                return i1 - i2;
        //            }
        //(5) public int compare(Object o1, Object o2)  返回的值>0还是<0
            //  会影响整个排序结果  这就充分体现了 接口编程+动态绑定+匿名内部类的综合使用
        //      将来的底层框架和源码的使用方式，会非常常见
        //Array.sort(arr);//默认排序方法
        //定制排序
        Arrays.sort(arr, new Comparator<Object>() {
            @Override
            public int compare(Object o1, Object o2) {
                Integer i1 = (Integer) o1;
                Integer i2 = (Integer) o2;
                return i1 - i2;
            }
        });
        for (int i = 0; i < arr.length; i++) {

            System.out.println(arr[i]);
        }
    }
}

```

### ArrayMethod02

```java
package com.study.arrays_;

import java.util.Arrays;
import java.util.List;

public class ArrayMethod02 {
    public static void main(String[] args) {
        Integer[] arr={-1,2,90,123,567};
        //binarySearch 通过二分搜索法进行查找，要求必须拍好
        //1.使用binarySearch 二叉查找
        //2.要求该数组是有序的，如果该数组是无序的，不能使用binarySearch
        //3.如果数组不存在该元素，就返回  return -(low+1);
        int index= Arrays.binarySearch(arr,233);
        System.out.println("index="+index);

        //copyOf 数组元素的复制
        //1.从arr数组中，拷贝 arr.length个元素到 newArr数组中
        //2.如果拷贝的长度>arr.length 就在新数组的后面 增加null
        //3.如果拷贝长度小于0，就抛出异常NegativeArraySizeException
        //4.该方法的底层使用的是 System.arraycopy()
        Integer[] newArr=Arrays.copyOf(arr,arr.length);
        System.out.println("==拷贝执行完毕后==");
        System.out.println(Arrays.toString(newArr));

        //ill数组元素的 填充
        Integer[] num=new Integer[]{9,3,2};
        Arrays.fill(num,99);
        System.out.println("==num数组填充后==");
        System.out.println(Arrays.toString(num));

        //equals 比较两个数组元素内容是否完全一致
        Integer[] arr2={1,2,90,123,567};
        //1.如果arr和arr2数组的元素一样，则方法返回true;
        //2.如果不是完全一样，就返回false
        boolean equals=Arrays.equals(arr,arr2);
        System.out.println("equals="+equals);

        //asList 将一组值，转换成list
        //1.asList方法，会将（2，3，4，5，6，1）数据转换成一个List集合
        //2.返回的asList 编译类型 List(接口)
        //3.aList 运行类型 java.util.Arrays#ArrayList,是Arrays类的
        //静态内部类 private static class ArrayList<E> extends AbstractList<E>
        //        implements RandomAccess, java.io.Serializable
        List asList =Arrays.asList(2,3,4,5,6,1);
        System.out.println("asList="+asList);
        System.out.println("asList的运行类型"+asList.getClass());



    }
}

```

### ArrayExercise

```java
package com.study.arrays_;

import java.util.Arrays;
import java.util.Comparator;

public class ArrayExercise {
    public static void main(String[] args) {
        /*
        案列：自定义Book类，里面包含name和price，按照price排序（从大到小）
        要求使用两种方式排序，有一个Book[] books=4本书对象

        使用前面学习过的传递 是西安Comparator接口匿名内部类，也成为定制排序。
        要求（1）price从大到小（2）price从小到大  (3)按照书名从大到小

         */
        Book[] books = new Book[4];
        books[0]=new Book("红楼梦",100);
        books[1]=new Book("三国演义",90);
        books[2]=new Book("新版西游记",5);
        books[3]=new Book("Java从入门到放弃",300);

        //（1）price从大到小

//        Arrays.sort(books, new Comparator<Book>() {
//            @Override
//            public int compare(Book o1, Book o2) {
//                Book book1=(Book) o1;
//                Book book2=(Book) o2;
//                double priceVal=book2.getPrice()-book1.getPrice();
//                //这里老师进行了一个转换
//                //如果发现返回结果和我们输出的不一致，就修改一下返回的1和-1
//                if(priceVal>0){
//                    return 1;
//                }else if(priceVal<0){
//                    return -1;
//                }else {
//                    return 0;
//                }
//            }
//        });

       // (2)要求price从小到大
//        Arrays.sort(books, new Comparator<Book>() {
//            @Override
//            public int compare(Book o1, Book o2) {
//                Book book1=(Book) o1;
//                Book book2=(Book) o2;
//                double priceVal=book2.getPrice()-book1.getPrice();
//                //这里老师进行了一个转换
//                //如果发现返回结果和我们输出的不一致，就修改一下返回的1和-1
//                if(priceVal>0){
//                    return -1;
//                }else if(priceVal<0){
//                    return 1;
//                }else {
//                    return 0;
//                }
//            }
//        });

        //(3)要求按照书名的长度
        Arrays.sort(books, new Comparator<Book>() {
            @Override
            public int compare(Book o1, Book o2) {
                Book book1=(Book) o1;
                Book book2=(Book) o2;
                return book2.getName().length()-book1.getName().length();
                //这里老师进行了一个转换
                //如果发现返回结果和我们输出的不一致，就修改一下返回的1和-1

            }
        });


        System.out.println(Arrays.toString(books));

    }
}
class Book{
    private String name;

    public Book(String name, double price) {
        this.name = name;
        this.price = price;
    }

    private double price;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    @Override
    public String toString() {
        return "Book{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
}
```

## System类

### System

```java
package com.study.system_;

import java.util.Arrays;

public class System_ {
    public static void main(String[] args) {


        //exit退出 当前程序
//        System.out.println("ok1");
//        //1.exit(0)表示程序退出
//        //2. 0表示一个状态，正常的状态
//        System.exit(0);
//        System.out.println("ok2");


        //arraycopy:复制数组元素，比较适合底层调用
        //一般使用Arrays.copyOf完成复制数组
        int []src={1,2,3};
        int []dest=new int[3];
        //主要搞清楚这五个参数的含义：
        //1.src: 源数组
        //2.srcPos: 从源数组的哪个索引位置开始拷贝
        //3.dest:  目标数组，即把源数组的数据拷贝到哪个数组
        //4.dest Pos: 把源数组的数据拷贝到 目标数组的哪个索引
        //5.length :从源数组拷贝多少个数据到目标数组
        System.arraycopy(src,0,dest,0,src.length);
        System.out.println("dest="+ Arrays.toString(dest));



        //currentTimeMillens:返回当前时间距离1970-1-1的毫秒数
        System.out.println(System.currentTimeMillis());
    }
}

```

## BigNum

### BigDecimal_

```java
package com.study.bignum;

import java.math.BigDecimal;

public class BigDecimal_ {
    public static void main(String[] args) {
        //当我们需要保存一个精度很高的数时， double 不够用
        //可以是BigDecimal
        double d=19999.1111111111111;
        BigDecimal bigDecimal = new BigDecimal("19343434.556526222222222222222222222");
        BigDecimal bigDecimal1 = new BigDecimal("23.562");
        System.out.println(bigDecimal);



        //1.如果对bigDecimal 进行加减运算，比如加减乘除，需要使用·对应的方法
        //2.创建一个需要操作的 BigDecimal 然后调用相应的方法即可
        System.out.println(bigDecimal.add(bigDecimal1));
        System.out.println(bigDecimal.subtract(bigDecimal1));
        System.out.println(bigDecimal.multiply(bigDecimal1));
        //System.out.println(bigDecimal.divide(bigDecimal1));//可能抛出异常
        //在调用divide 方法时，指定精度时，BigDecimal.ROUND_CEILING
        //如果有无限循环小数，就会保留分子的精度
        System.out.println(bigDecimal.divide(bigDecimal1,BigDecimal.ROUND_CEILING));//


    }
}

```

### BigInteger_

```java
package com.study.bignum;

import java.math.BigInteger;

public class BigInteger_ {
    public static void main(String[] args) {


        //当我们 编程中，需要处理很大的整数，long 不够用
        //可以使用BigInteger的类来搞定
        long l=237888888888l;
        System.out.println("l="+l);

        BigInteger bigInteger = new BigInteger("5555555555555555555555555555555555555555555555555");
        BigInteger bigInteger2 = new BigInteger("100");
        System.out.println(bigInteger);


        //1.在对 BigInteger 进行加减乘除的时候，需要使用对应的方法，不能直接加减乘除
        //2.可以创建一个 要操作的BigInteger 然后进行相应操作
        BigInteger add=bigInteger.add(bigInteger2);
        System.out.println(add);
        BigInteger subtract=bigInteger.subtract(bigInteger2);
        System.out.println(subtract);//减
        BigInteger multiply=bigInteger.multiply(bigInteger2);
        System.out.println(multiply);//乘法
        BigInteger divide = bigInteger.divide(bigInteger2);
        System.out.println(divide);//除法

    }
}

```

## Date类

### Date01

```java
package com.study.date_;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.SimpleTimeZone;

public class Date01 {
    public static void main(String[] args) throws ParseException {

        //1.获取当前系统时间
        //2.这里的Date类是在java.util包
        //3.默认输出的日期格式是国外的方式，因此通常需要对格式进行转换
        Date d1 = new Date();
        System.out.println("d当前日期="+d1);
        Date d2 = new Date(6925155);
        System.out.println("d2="+d2);

        //1.创建 SimpleDateFormat对象，可以指定相应的格式
        //2.这里的格式使用字母是规定好，不能乱写

        SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 hh:mm:ss E");
        String format =sdf.format(d1);//format:将日期转换成指定格式的字符串
        System.out.println("当前日期="+format);

        //1.可以把一个格式化的字符串String转化为 Date
        //2.得到的Date 仍然在输出时，还是按照国外的形式，如果希望指定格式输出，需要转换
        //3.在把一个String转换成Date,使用的 sdf 格式需要和你给的String的格式一样，否则会抛出异常
        String s="1996年01月01日 10:20:30 星期一";
        Date parse=sdf.parse(s);
        System.out.println("parse="+parse);



    }
}
class Dog{
    private String name;
    private int age;

    public Dog(String name, int age) {
        this.name = name;
        this.age = age;
    }
    public void cry(){

    }
    class Air{

    }
    public void setAddress(String address){

    }
    public double getSalary(){
        return 1.1;
    }

}
```

### Calendar_

```java
package com.study.date_;

import java.util.Calendar;

public class Calendar_ {
    public static void main(String[] args) {
        //1.Calender是一个抽象类，并且构造器是private
        //2.可以通过 getInstance()来获取实例
        //3.提供大量的方法和字段提供给程序员
        //4.Calendar没有提供相应的格式化的类，因此需要程序员自己组合来输出(灵活)
        //5.如果我们需要按照 24小时进制来获取时间， Calender.HOUR==改成=> Calender.HOUR_OF_DAY

        Calendar c=Calendar.getInstance();//创建日历对象//比较简单，自由
        System.out.println("c="+c);
        //2.获取  日历对象的某个日历字段
        System.out.println("年:"+c.get(Calendar.YEAR));
        //这里为什么要加 1 因为Calender 返会月的时候，是按照0开始编号
        System.out.println("月:"+(c.get(Calendar.MONTH)+1));
        System.out.println("日:"+c.get(Calendar.DAY_OF_MONTH));
        System.out.println("小时:"+c.get(Calendar.HOUR));
        System.out.println("分钟:"+c.get(Calendar.MINUTE));
        System.out.println("秒:"+c.get(Calendar.SECOND));
        //Calender 没有专门的格式化方法，所以需要程序员自己来组合显示
        System.out.println(c.get(Calendar.YEAR)+"-"+(c.get(Calendar.MONTH)+1)+"-"+
                c.get(Calendar.DAY_OF_MONTH)+"  "+c.get(Calendar.HOUR_OF_DAY)+":"+
                c.get(Calendar.MINUTE)+":"+c.get(Calendar.SECOND));



    }
}

```

### LocalDate_

```java
package com.study.date_;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class LocalDate_ {
    public static void main(String[] args) {
        //第三代日期
        //1.我们使用now() 返回当前日期时间的对象
        LocalDateTime ldt=LocalDateTime.now();
        //LocalDate().now(); 年月日
        // LocalTime.now() 时分秒
        System.out.println(ldt);


        //2.使用DateTimeFormatter 对象来进行格式化
        //创建 DateTimeFormatter对象
        DateTimeFormatter dateTimeFormatter=DateTimeFormatter.ofPattern("yyyy年MM月dd日 HH:mm:ss E");
        String format=dateTimeFormatter.format(ldt);
        System.out.println("格式化的日期="+format);

        System.out.println("年="+ldt.getYear());
        System.out.println("月="+ldt.getMonth());
        System.out.println("月="+ldt.getMonthValue());
        System.out.println("日="+ldt.getDayOfMonth());
        System.out.println("时="+ldt.getHour());
        System.out.println("分="+ldt.getMinute());
        System.out.println("秒+"+ldt.getSecond());


    }
}

```

### Instant_

```java
package com.study.date_;

import java.time.Instant;
import java.util.Date;

public class Instant_ {
    public static void main(String[] args) {
        //1.通过静态方法 now() 来表示当前时间戳的对象
        Instant now = Instant.now();
        System.out.println(now);
        //2.通过from可以把Instant 转换成Date
        Date date=Date.from(now);
        //3.通过date的toInstant() 可以把date 转换成Instant对象
        Instant instant=date.toInstant();
    }
}

```

## homework

### Homework01

```java
package com.study.homework;

public class Homework01 {
    public static void main(String[] args) {
        /*
        (1)将字符串中中指定部分进行反转，比如将“abcdef”反转成“aedcbf"
        (2)编写方法 public static String reverse(String str,int start,int end)搞定

         */
        String str = "abcdef";
        System.out.println("====交换前====");
        System.out.println(str);
        try {
            str = reserve(str, 1, 4);
        } catch (Exception e) {
            System.out.println(e.getMessage());
            return;
        }
        System.out.println("====交换后====");
        System.out.println(str);


    }

    public static String reserve(String str, int start, int end) {
        //对输入的参数做一个验证
        //重要的编程技巧
        //（1）写出正确的情况
        //（2）然后取反即可
        if(!(str!=null&&start>=0&&end>start&&end<str.length())){
            throw new RuntimeException("参数不正确");

        }
        char[] chars = str.toCharArray();
        char temp = ' ';
        for (int i = start, j = end; i < j; i++,j--) {
            temp = chars[i];
            chars[i] = chars[j];
            chars[j] = temp;

        }
        //使用chars交换后的 重新构建一个String返回即可
        return new String(chars);

    }
}


```

### Homework02

```java
package com.study.homework;

public class Homework02 {
    public static void main(String[] args) {
        String name="Jack";
        String pwd="123456";
        String email="Jack@sogou.com";
        try {
            userRegister(name,pwd,email);
            System.out.println("恭喜你注册成功！");
        }catch (Exception e){
            System.out.println(e.getMessage());
        }


    }

    /**
     * 输入用户名、密码、邮箱，如果有信息录入正确，则提示注册成功，否则生成异常对象
     * 要求：
     * （1）用户长度为2或3或4
     * （2）密码的长度为6，要求是全是数字
     * （3）邮箱中包含@和. 并且@在.前面
     * <p>
     * 思路分析：
     * （1）先编写方法 userRegister(String name,String pwd,String email){}
     * (2)针对输入的内容进行校验，如果发现有问题，就抛出异常，给出提示
     * (3)单独写方法，判断密码是否全部是数字字符 boolean
     */

    public static void userRegister(String name, String pwd, String email) {




        //再加入一些校验
        if(!(name!=null&&pwd!=null&email!=null)){
            throw new RuntimeException("参数不能为空");
        }
        //过关斩将
        //第一关
        int userLength = name.length();
        if (!(userLength >= 2 && userLength <= 4)) {
            throw new RuntimeException("用户长度为2或3或4");

        }

        //第二关
        if (!(pwd.length() == 6 && isDigital(pwd))) {
            throw new RuntimeException("密码的长度为6，要求是全是数字");

        }
        //第三关
        int i=email.indexOf('@');
        int j=email.indexOf('.');
        if(!(i>0&&j>1)){
            throw new RuntimeException("邮箱中包含@和.  并且@在.的前面");

        }

    }

    //单独写方法，判断密码是否全部是数字字符 boolean
    public static boolean isDigital(String str) {
        char[] chars = str.toCharArray();
        for (int i = 0; i < chars.length; i++) {
            if (chars[i] < '0' || chars[i] > '9') {
                return false;
            }


        }
        return true;
    }
}


```

### Homework03

```java
package com.study.homework;

import java.util.Locale;

public class Homework03 {
    public static void main(String[] args) {
        String name="Feng Rong Xu";
        printName(name);

    }
    /**
     * 编写方法：完成输出格式要求的字符串
     * 编写java程序，输入形式为：Feng Rong Xu的人名，以 Xu,Feng .R的形式打印
     * 出来，其中.R是中间单词的首字母
     *
     * 思路分析
     * （1）对输入的字符串进行分割split(" ")
     * (2)对得到的String[] 进行格式化String.format()
     * （3）对输入的字符串校验即可
     *
     *
     */
    public static void printName(String str){
        if(str==null){
            System.out.println("str 不能为空");
            return;
        }
        String[] names=str.split(" ");
        if(names.length!=3){
            System.out.println("输入的字符格式不对");
            return;
        }
        String format = String.format("%s,%s .%c", names[2], names[1], names[1].toUpperCase().charAt(0));
        System.out.println(format);


    }
}

```

### Homework04

```java
package com.study.homework;

import java.awt.datatransfer.StringSelection;

public class Homework04 {
    public static void main(String[] args) {
        String str="abcFRX  U 133";
        countStr(str);
    }
    /**
     * 输入字符串，判断里面有多少个大写字母，多少个小写字母，多少个数字
     * 思路分析
     * （1）遍历字符串，如果 char在'0'~'9'就是一个数字
     * （2）如果 char 在'a'~'z' 就是一个小写字母
     * （3）如果 char 在'A'~'z' 就是一个大写字母
     * （4）使用三个变量来记录 统计结果
     */
    public static void countStr(String str){
        if(str==null){
            System.out.println("输入不能为null");
            return;
        }
        int strLen=str.length();
        int numCount=0;
        int lowerCount=0;
        int upperCount=0;
        int otherCount=0;
        for (int i = 0; i < str.length(); i++) {
            if(str.charAt(i)>='0'&&str.charAt(i)<='9'){
                numCount++;
            }else if(str.charAt(i)>='a'&&str.charAt(i)<='z'){
                 lowerCount++;
            }else if(str.charAt(i)>='A'&&str.charAt(i)<='Z'){
                upperCount++;
            }else {
                otherCount++;

            }

        }
        System.out.println("数字有 "+numCount);
        System.out.println("小写字母有 "+lowerCount);
        System.out.println("大写字母有 "+upperCount);
        System.out.println("其他有 "+otherCount);
    }
}

```

### Homework05

```java
package com.study.homework;

public class Homework05 {
    public static void main(String[] args) {
        String s1="hh";
        Animal a=new Animal(s1);
        Animal b=new Animal(s1);
        System.out.println(a==b);
        System.out.println(a.equals(b));
        System.out.println(a.name==b.name);

        String s4=new String("hh");
        String s5="hh";

        System.out.println(s1==s4);
        System.out.println(s4==s5);

        String t1="hello"+s1;
        String t2="hellohh";
        System.out.println(t1.intern()==t2);

    }
}
class Animal{
    String name;

    public Animal(String name) {
        this.name = name;
    }
}

```



