# JAVA12

## object_

### Equals01

```java
package com.study6object_;

public class Equals01 {
    public static void main(String[] args) {
        A a = new A();
        A b = a;
        A c = b;
        System.out.println(a == c);//true
        System.out.println(b == c);//true
        B bObj = a;
        System.out.println(bObj == c);//true
        int n = 10;
        double m = 10.0;
        System.out.println(n == m);
        //把光标
        "hello".equals("abc");
        //即Object类的equals方法默认就是比较对象地址是否相同
        //也就是判断两个对象是不是同一个对象
        //public boolean equals(Object obj){
        //return (this==obj);
        //}
        //从源码可以看到Integer也重写了Object的equals方法，
        /*
        public boolean equals(Object obj) {
        if (obj instanceof Integer) {
            return value == ((Integer)obj).intValue();
        }
        return false;
    }
         */
        Integer integar1 = new Integer(1000);
        Integer integer2 = new Integer(1000);
        System.out.println(integar1==integer2);//false
        System.out.println(integar1.equals(integer2));//true


        String str1=new String("frx");
        String str2=new String("frx");
        System.out.println(str1==str2);//false
        System.out.println(str1.equals(str2));//true



    }
}
class B{

}



class A extends B{

}
```

### EqualsExercise01

```java
package com.study6object_;

public class EqualsExercise01 {
    public static void main(String[] args) {
        Person person1 = new Person("jack", 10, '男');
        Person person2= new Person("jack", 10, '男');
        System.out.println(person1.equals(person2));//true
    }
}
//判断两个Person对象的内容是否相等
//如果两个Person对象的各个属性值 都一样，则返回true，反之false
class Person{//extends Object
    private String name;
    private int age;
    private char gender;

    //重写Object的equals方法
   public boolean equals(Object obj){
       //判断结果比较的两个对象是同一个对象，则直接返回true
       if(this==obj){
           return true;
       }
       //类型判断
       if(obj instanceof Person){//是Person 我们才比较
        //进行向下转型,因为我需要得到Object的各个属性
           Person p=(Person)obj;
           return this.name.equals(p.name)&&this.age==p.age&&this.gender==p.gender;


       }
       //如果不是Person，则直接返回false
       return false;
   }
    public Person(String name, int age, char gender) {
        this.name = name;
        this.age = age;
        this.gender = gender;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public char getGender() {
        return gender;
    }

    public void setGender(char gender) {
        this.gender = gender;
    }
}

```

### EqualsExercise02

```java
package com.study6object_;

public class EqualsExercise02 {
    public static void main(String[] args) {
        Person_ p1 = new Person_();
        p1.name="frx";
        Person_ p2 = new Person_();
        p2.name="frx";
        System.out.println(p1==p2);//false
        System.out.println(p1.name.equals(p2.name));//T
        System.out.println(p1.equals(p2));//false

        String s1=new String("abc");
        String s2=new String("abc");
        System.out.println(s1.equals(s2));//T
        System.out.println(s1==s2);//F


    }
}
class Person_{
    public String name;
}





```

### Finalize_

```java
package com.study6object_;

public class EqualsExercise02 {
    public static void main(String[] args) {
        Person_ p1 = new Person_();
        p1.name="frx";
        Person_ p2 = new Person_();
        p2.name="frx";
        System.out.println(p1==p2);//false
        System.out.println(p1.name.equals(p2.name));//T
        System.out.println(p1.equals(p2));//false

        String s1=new String("abc");
        String s2=new String("abc");
        System.out.println(s1.equals(s2));//T
        System.out.println(s1==s2);//F


    }
}
class Person_{
    public String name;
}





```

### HashCode

```java
package com.study6object_;

public class HashCode_ {
    public static void main(String[] args) {
        AA aa = new AA();
        AA aa2 = new AA();
        AA aa3=aa;
        System.out.println("aa.hashcode=="+aa.hashCode());
        System.out.println("aa2.hashcode=="+aa2.hashCode());
        System.out.println("aa3.hashcode=="+aa3.hashCode());
    }

}
class AA{

}
```

### ToString_

```java
package com.study6object_;

public class ToString_ {
    public static void main(String[] args) {
/*
Object toString（） 方法的源码
（1）getClass().getName()//全类名 包名加类名
（2）Integer.toHexString(hashCode()将 对象的Hashcode值转为 十六进制字符串
public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }
 */


        Monster monster = new Monster("小妖怪", "巡山", 1000);
        System.out.println(monster.toString()+"\thashcode="+monster.hashCode());
        System.out.println("==当直接输出一个对象时，toString方法会被默认的调用");
        System.out.println(monster);//等价monster.toString()
    }
}
class Monster{
    String name;
    String job;
    private double sal;

    public Monster(String name, String job, double sal) {
        this.name = name;
        this.job = job;
        this.sal = sal;
    }
    //重写toString方法，输出对象的属性
    //使用快捷键即可alt+insert

    @Override
    public String toString() {//默认重写后 一般是把对象的属性输出出来
        return "Monster{" +
                "name='" + name + '\'' +
                ", job='" + job + '\'' +
                ", sal=" + sal +
                '}';
    }
}

```





