# JAVA10

## Override_

### Animals

```java
package com.study4.override_;

public class Animal {
    //1.因为Dog是Animals的子类
    //2.Dog的cry方法和Animals的cry定义形式一样（名称、返回类型、参数）
    //3.这时我们就说Dog的cry方法，重写了Animals的cry方法
    public void cry(){
        System.out.println("动物叫唤...");
    }
    public Object m1(){
        return null;
    }
    public String m2(){
        return null;
    }

//      public BBB m3(){
//        return null;
//      }
      private void eat(){

      }


}

```

### Dog

```java
package com.study4.override_;

public class Dog extends Animal {
    public void cry() {
        System.out.println("狗叫唤...");
    }

    //细节：子类方法的返回类型和父类方法返回类型一样
    //     或者是父类返回类型的子类VT比如 父类 返回类型是Object，
    //     子类方法返回类型是String
    public String m1() {
        return null;
    }
    //这里Object不是String的子类，编译报错
//    public Object m2(){
//        return null;
//    }

    public BBB m3() {
        return null;
    }
    //细节：子类方法不能缩小父类的访问权限
    //public>protected>默认>private
    public void eat(){

    }

}
    class AAA {

    }

    class BBB extends AAA {

    }

```

### Override01

```java
package com.study4.override_;

public class Override01 {
    //演示方法重写情况
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.cry();//ctrl +b定位
    }

}
//      名称         发生范围       方法名        形参列表                返回类型                           修饰符
//---------------------------------------------------------------------------------------------------------------
// 重载(Overload)      本类       必须一样       类型、个数                 无要求                            无要求
//                                            或顺序至少有
//                                            一个不同
//————————————————————————————————————————————————————————————————————————————————————————————--------------------
//重写(Override)      父子类       必须一样         相同             子类重写的方法，返回                   子类方法不能
//                                                                的类型和父类返回的                    缩小父类的访问
//                                                                类型一致，或者是其子类                  范围
```



### exercise

#### Person

```java
package com.study4.override_.excrcise;

public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    public String say(){
        return "name="+name+" age="+age;
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
}

```

#### Student

```java
package com.study4.override_.excrcise;

public class Student extends Person{
    private int id;
    private double score;

    public Student(String name, int age, int id, double score) {
        super(name, age);//这里会调用父类构造器
        this.id = id;
        this.score = score;
    }
    //say
    public String say(){//这里体现super的好处
        return super.say()+" id="+id+" score="+score;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public double getScore() {
        return score;
    }

    public void setScore(double score) {
        this.score = score;
    }
}

```

#### OverrideExercise

```java

package com.study4.override_.excrcise;

public class OverrideExercise {
    public static void main(String[] args) {
        Person jack = new Person("Jack", 10);
        System.out.println(jack.say());

        Student smith = new Student("smith", 20, 123456, 99.8);
        System.out.println(smith.say());
    }
}

```

