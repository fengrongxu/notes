# JAVA11

## poly_

### animal

#### Animal

```java
package com.study5poly.poly_.animal;

public class Animal {
    private String name;

    public Animal(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```

#### Food

```java
package com.study5poly.poly_.animal;

public class Food {
    private String name;

    public Food(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```

#### Bone

```java
package com.study5poly.poly_.animal;

public class Bone extends Food {
    public Bone(String name) {
        super(name);
    }
}

```

#### Rice

```java
package com.study5poly.poly_.animal;

public class Rice extends Food {
    public Rice(String name) {
        super(name);
    }
}

```

#### Dog

```java
package com.study5poly.poly_.animal;

public class Dog extends Animal {
    public Dog(String name) {
        super(name);
    }
}

```

#### Fish

```java
package com.study5poly.poly_.animal;

public class Fish extends Food {
    public Fish(String name) {
        super(name);
    }
}

```

#### Pig

```java
package com.study5poly.poly_.animal;


public class Pig extends Animal {
    public Pig(String name) {
        super(name);
    }
}

```



#### Cat

```java
package com.study5poly.poly_.animal;

public class Cat extends Animal {
    public Cat(String name) {
        super(name);
    }
}

```

#### Monster

```java
package com.study5poly.poly_.animal;

public class Master {
    private String name;

    public Master(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
    //使用多态机制，可以统一的管理主人喂食的问题
    //animal 编译类型是Animal ，可以指向（接受）Animal子类的对象
    //food 编译类型是Food,可以指向 food子类的对象
    public void feed(Animal animal, Food food){
        System.out.println("主人 "+name+" 给"+animal.getName()+" 喂 "+food.getName());
    }





    //主人给小狗喂骨头
//    public void feed(Dog dog,Bone bone){
//        System.out.println("主人 "+name+" 给"+dog.getName()+" 喂 "+bone.getName());
//
//    }
//    //主人给小猫喂黄花鱼
//    public void feed(Cat cat,Fish fish){
//        System.out.println("主人 "+name+" 给"+cat.getName()+" 喂 "+fish.getName());
//
//    }

}

```

#### Poly01

```java
package com.study5poly.poly_.animal;

public class Poly01 {
    public static void main(String[] args) {
        Master tom = new Master("Tom");
        Dog dog= new Dog("大黄");
        Bone bone = new Bone("大棒骨");
        tom.feed(dog,bone);
        Cat cat = new Cat("小花猫");
        Fish fish = new Fish("黄花鱼");
        System.out.println("=====================");
        tom.feed(cat,fish);
        //添加 给小猪喂米饭
        Pig pig = new Pig("小花猪");
        Rice rice = new Rice("米饭");
        System.out.println("=====================");
        tom.feed(pig,rice);
    }
}

```

### detail

#### Animal

```java
package com.study5poly.poly_.detail_;

public class Animal {
    String name="动物";
    int age=10;
    public void sleep(){
        System.out.println("睡");
    }
    public void run(){
        System.out.println("跑");
    }
    public void eat(){
        System.out.println("吃");
    }
    public void show(){
        System.out.println("hello.你好");
    }

}

```

#### Cat

```java
package com.study5poly.poly_.detail_;

public class Cat extends Animal{
    public void eat(){//方法重写
        System.out.println("猫吃鱼");
    }
    public void catchMouse(){//Cat特有的方法
        System.out.println("猫抓老鼠");
    }
}

```

#### Dog

```java
package com.study5poly.poly_.detail_;

public class Dog extends Animal{//Dog是Animal的子类
    public void sleep(){
        System.out.println("狗在睡...");
    }

}

```

#### PolyDetail

```java
package com.study5poly.poly_.detail_;

public class PolyDetail {
    public static void main(String[] args) {
        //向上转型 ：父类的引用指向了子类的对象
        //语法：父类类型引用名=new 子类类型();
        Animal animal=new Cat();
        Object pbj=new Cat();//ok
        //向上转型调用的方法的规则如下
        //可以调用父类中的所有成员（需遵守访问权限）
        //但是不能调用子类特有的成员
        //因为在编译阶段，能调用那些成员，是由编译类型来决定的
        //animal.catchMouse();//错误
        //最终运行 效果看子类的实现  即调用方法时，按照从子类开始查找方法调用
        //规则与前面我们讲的方法调用规则一致。
        animal.eat();//猫吃鱼...
        animal.run();//跑
        animal.show();//hello.你好
        animal.sleep();//睡
        //希望调用Cat的catchMouse方法
        //多态的向下转型
        //（1）语法：子类类型 引用名=（子类类型）父类引用；
        //cat的编译类型  Cat 运行类型是Cat
        Cat cat=(Cat)animal;
        cat.catchMouse();
        //（2）要求父类的引用必须指向的是当前目录类型的对象
//        Animal animal1=new Dog();
//        Dog dog=(Dog)animal1;
//        dog.sleep();
    }
}

```

### PolyDetail02

```java
package com.study5poly.poly_.detail_;

public class PolyDetail02 {
    public static void main(String[] args) {
         //属性没有重写之说！属性的值看编译类型
        Base base=new Sub();//向上转型
        System.out.println(base.count);//?//10
        Sub sub = new Sub();
        System.out.println(sub.count);//20


    }
}
class Base{//父类
    int count=10;//属性

}
class Sub extends Base{//子类
    int count=20;//属性
}

```

### dynamic_

```java
package com.study5poly.poly_.dynamic_;

public class DynamicBinding {
    public static void main(String[] args) {
        A a=new B();
        System.out.println(a.sum());//40->30
        System.out.println(a.sum1());//30
    }
}
class A{//父类
    public int i=10;
    public int sum(){
        return getI()+10;//20+10
    }
        public int sum1(){
       return i+10;
    }
    public int getI(){//父类get1
        return i;
    }
}
class B extends A {
    public int i = 20;

//        public int sum(){
//       return i+20;
//    }
    public int getI() {//子类get1（）

        return i;
    }

//   public int sum1() {
//        return i + 10;
//    }
}
//java的动态绑定机制
//1.当调用对象方法的时候，该方法回合该对象的内存地址/运行类型绑定
//2.当调用对象属性时，没有动态绑定机制，哪里声明，哪里使用
```

### polyarr_

#### Person

```java
package com.study5poly.poly_.polyarr_;

public class Person {
    String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
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
    public String say(){//返回名字和年龄
        return name+"\t"+age;
    }
}

```

#### Student

```java
package com.study5poly.poly_.polyarr_;

public class Student extends Person{
    private double score;

    public Student(String name, int age, double score) {
        super(name, age);
        this.score = score;
    }

    public double getScore() {
        return score;
    }

    public void setScore(double score) {
        this.score = score;
    }
    public String say(){
        return "学生 "+super.say()+"\tscore="+score;

    }
    //特有方法
    public void study(){
        System.out.println("学生"+getName()+"正在学Java...");
    }
}

```

#### Teacher

```java
package com.study5poly.poly_.polyarr_;

public class Teacher extends Person{
    private double salary;

    public Teacher(String name, int age, double aslary) {
        super(name, age);
        this.salary = aslary;
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }
    //重写say方法


    public String say() {
        return "老师 "+super.say()+"\tsalary="+salary;
    }
    //特有方法
    public void teach(){
        System.out.println("老师 "+getName()+"正在讲Java课程");
    }
}

```

#### PolyArray

```java
package com.study5poly.poly_.polyarr_;

public class PloyArray {
    public static void main(String[] args) {
//应用实例：现有一个继承机构如下：要求创建1个Person对象。
        //2个Student 对象和2个Teacher对象，统一放在数组中，并调用每个对象say方法
        Person person[] = new Person[5];
        person[0] = new Person("jack", 20);
        person[1] = new Student("mary", 18, 100);
        person[2] = new Student("smith", 19, 30.1);
        person[3] = new Teacher("scott", 30, 20000);
        person[4] = new Teacher("king", 50, 25000);
//循环遍历多态数组，调用say()方法
        for (int i = 0; i < person.length; i++) {
            //person[i]编译类型 是Person ，运行由jvm机来判断
            //动态绑定机制
            System.out.println(person[i].say());
            //这里
            if (person[i] instanceof Student) {//判断person[i]的运行类型是不是Student
             Student student=(Student)person[i];//向下转型
                student.study();
            }else if(person[i] instanceof Teacher){
                Teacher teacher=(Teacher) person[i];
                teacher.teach();
            }else if(person[i] instanceof Person){
            }else {
                System.out.println("你的类型有误，请自己检查");
            }
        }

    }
}
```

### Ployparameter_

#### Employee

```java
package com.study5poly.poly_.polyparameter_;

public class Employee {
    private String name;
    private double salary;

    public Employee(String name, double salary) {
        this.name = name;
        this.salary = salary;
    }
    //得到年工资的方法
    public double getAnnual(){
        return 12*salary;
    }


    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double  getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }
}

```

#### Manager

```java
package com.study5poly.poly_.polyparameter_;

public class Manager extends Employee{
   private double bonus;

    public Manager(String name, double salary, double bonus) {
        super(name, salary);
        this.bonus = bonus;
    }

    public double getBonus() {
        return bonus;
    }

    public void setBonus(double bonus) {
        this.bonus = bonus;
    }
    public void manage(){
        System.out.println("经理 "+getBonus()+"is Manager");
    }
    //重写获取年薪的方法

    @Override
    public double getAnnual() {
        return super.getAnnual()+bonus;
    }
}

```

#### Worker

```java
package com.study5poly.poly_.polyparameter_;

public class Worker extends Employee{
    public Worker(String name, double salary) {
        super(name, salary);
    }
    public void work(){
        System.out.println("普通员工 "+getName()+" is working");
    }

    @Override
    public double getAnnual() {//因为普通员工没有其他收入，则直接调用父类
        return super.getAnnual();
    }
}

```

#### PloyParameterr

```java
package com.study5poly.poly_.polyparameter_;

public class PolyParameter {
    public static void main(String[] args) {
        Worker tom = new Worker("Tom", 2500);
       Manager MILAN= new Manager("MILAN",5000,200000);
        PolyParameter polyParameter = new PolyParameter();
        polyParameter.showEmpAnnual(tom);
        polyParameter.showEmpAnnual(MILAN);
        polyParameter.testWork(tom);
        polyParameter.testWork(MILAN);



    }

//showEmpAnnual(Employee e)
    //实现获取任何员工对象的年工资，并在main方法中调用该方法
    public void showEmpAnnual(Employee a){
        System.out.println(a.getAnnual());//动态绑定机制
    }
    //添加一个方法，testWork ，如果是普通员工，则调用work方法，如果是经理，就调用manager方法
     public void  testWork(Employee e){
        if(e instanceof Worker){
            ((Worker) e).work();//向下转型
        }else if(e instanceof Manager){
            ((Manager) e).manage();//向下转型
        }
     }
}
```

### PolyDetail03

```java
package com.study5poly.poly_;

public class PolyDetail03 {
    public static void main(String[] args) {
        BB bb = new BB();
        //instanceof比较操作符 ，用于判断对象的类型是否为XX类型或XX类型的子类型
        System.out.println(bb instanceof BB);//true
        System.out.println(bb instanceof AA);//true
        //aa编译类型AA  运行类型为BB
        AA aa=new BB();
        System.out.println(aa instanceof AA);//true
        System.out.println(aa instanceof BB);//true
        Object obj=new Object();
        System.out.println(obj instanceof AA);//false
        String str="hello";
      //  System.out.println(str instanceof AA);
        System.out.println(str instanceof Object);//true

    }
}
class AA{

}
class BB extends AA{

}
```



```java
package com.study5poly.poly_.polyparameter_;

public class Manager extends Employee{
   private double bonus;

    public Manager(String name, double salary, double bonus) {
        super(name, salary);
        this.bonus = bonus;
    }

    public double getBonus() {
        return bonus;
    }

    public void setBonus(double bonus) {
        this.bonus = bonus;
    }
    public void manage(){
        System.out.println("经理 "+getBonus()+"is Manager");
    }
    //重写获取年薪的方法

    @Override
    public double getAnnual() {
        return super.getAnnual()+bonus;
    }
}

```

### 







```java
package com.study5poly.poly_.detail_;

public class Dog extends Animal{//Dog是Animal的子类
    public void sleep(){
        System.out.println("狗在睡...");
    }

}

```

### 







