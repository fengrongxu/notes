# JAVA09

## encap

### Account

```java
package com.study2encap;


/*
创建程序，在其中定义两个类，Account和AccountTest类体会Java的封装性
Account类要求具有属性：姓名（长度为2位3位或4位）、余额（必须>20）
密码（必须是六位），如果不满足，则给出提示信息，并给默认值（程序员自己定）
通过setXxx的方法给Account的属性赋值。
在AccountTest中测试
 */
public class Account {
    //为了封装，将三个属性设置为private
    private String name;
    private double balance;
    private String pwd;
//提供两个构造器
    public Account() {
    }

    public Account(String name, double balance, String pwd) {
       setBalance(balance);
       setPwd(pwd);
       setName(name);

    }

    public String getName() {
        return name;
    }
//姓名（长度为2位3位4位）
    public void setName(String name) {
        if(name.length()>=2&&name.length()<=4){
            this.name = name;
        }else{
            System.out.println("名字长度为2位3位4位,默认 无名");
            this.name="无名人";
        }

    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        if(balance>20) {
            this.balance = balance;
        }else {
            System.out.println("余额不足，默认0");
        }
    }

    public String getPwd() {
        return pwd;
    }

    public void setPwd(String pwd) {
        if(pwd.length()==6){
            this.pwd = pwd;
        }else{
            System.out.println("密码长度应为六位 默认为000000");
            this.pwd="000000";
        }

    }
    //显示账号信息
    public void showInfo() {
        //可以增加权限的校检
        System.out.println("账号信息="+name+" 余额="+balance+" 密码"+pwd);
//        if(){
//            System.out.println("账号信息="+name+" 余额="+balance+" 密码"+pwd);
//        }else {
//            System.out.println("你无权查看...");
//        }
    }
}

```

### TestAccount

```java
package com.study2encap;

public class TestAccount {
    public static void main(String[] args) {
        //创建Account
        Account account = new Account();
        account.setName("Jacksmith");
        account.setBalance(60);
        account.setPwd("123456");
        account.showInfo();
        Account account1 = new Account("smith",600,"666666");
        System.out.println("=====smith的信息======");
        account.showInfo();
    }
}

```

### Encapsulation01

```java
package com.study2encap;

public class Encapsulation01 {
    public static void main(String[] args) {
        Person person = new Person();
        person.setName("冯荣旭和冯荣旭");
        person.setAge(30);
        person.setSalary(30000);
        System.out.println(person.info());
        System.out.println(person.getSalary());
        //如果我们直接使用构造器 指定属性
        Person smith = new Person("smith", 2000, 50000);
        System.out.println("======smith的信息======");
        System.out.println(smith.info() );
    }
}
/*
不能随便查看别人的年龄，工资等隐私，名字公开
要求：年龄合理 在1-120， name在2-6字符之间
 */
class Person{
    public String name;//名字公开
    private int age; //age私有
    private double salary;//工资私有
    //构造器 alt+insert
     public Person(){
     }
     //有三个属性的构造器
    public Person(String name, int age, double salary) {
//        this.name = name;
//        this.age = age;
//        this.salary = salary;
        //我们尅将方法写在构造器中，这样仍然可以验证数据
        setName(name);
        setAge(age);
        setSalary(salary);

    }


    //自己写 setXxx和 getsetXxx 太慢 我们使用快捷键 alt+insert
    //然后根据要求 写我们的代码

    public String getName() {
        return name;
    }

    public void setName(String name) {
        //加入对数据的校验，相当于增加了业务逻辑
        if(name.length()>=2&&name.length()<=6){
            this.name=name;
        }else{
            System.out.println("名字的长度不对，需在2-6字符");
            this.name="无名人";
        }

    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        //判断
        if(age>=1&&age<=120){//如果是合理范围
            this.age=age;
        }else{
            System.out.println("你设置的年龄不对，年龄需要在1-120之间，给默认年龄18");
            this.age = 18;//给默认年龄18
        }
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        //可以这里增加对当前对象的权限判断
        this.salary = salary;
    }
//写一个方法，返回属性信息
    public String info(){
        return "信息为 name="+name+"  age="+age+" salary= "+salary;
    }

        }
```

