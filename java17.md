# Java17

## annotation_

### Override_

```java
package com.study.study14annotation_;

public class Override_ {
    public static void main(String[] args) {

    }
}
class Father{
    public void fly(){
        System.out.println("Father...");
    }
}
class Son extends Father{
    @Override
    //1. @Override注解放在fly方法上，表示子类重写了父类的fly()方法
    //2.如果没有写@Override注解，还是会重写
    //3.如果写了Override 注解，编译器就回去检查方法是否真的重写了父类的方法
    //如果的确重写 编译通过 如果没有构成重写 则编译错误
    //4.Override的定义
    //如果发现 @interface 表示一个注解类
    /*
     * @Target(ElementType.METHOD)  //@Target修饰注解的注解 称为源注解
     * @Retention(RetentionPolicy.SOURCE)
     * public @interface Override {
     * }
     */
    public void fly() {
        System.out.println("Son...");
    }
}
```

### SuppressWarnings_



```java
package com.study.study14annotation_;


import java.util.ArrayList;
import java.util.List;

@SuppressWarnings({"all"})
public class SuppressWarnings_ {
    //1.当我们不希望看到这些警告的时候，可以使用SuppressWarnings注解来抑制警告信息
    //2.在{""}中，可以写入你希望抑制（不显示）警告信息
    //3.all
    //4关于SuppressWarnings作用范围是和你放置的位置相关
    //  比如@SuppressWarnings放置在main 方法，那么抑制警告的范围就是 main
    //通常我们可以放置具体的语句，方法，类
    //5.源码
   /* @Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})//放置的位置
    @Retention(RetentionPolicy.SOURCE)
    public @interface SuppressWarnings {
        String[] value(); //该注解类有数组
    }*/

    @SuppressWarnings({"all"})
    public static void main(String[] args) {
        List list=new ArrayList();
        list.add("");
        list.add("");
        list.add("");
        int i;
        System.out.println(list.get(1));

    }
}

```

### Deprecated_

```java
package com.study.study14annotation_;


public class Deprecated_ {
    public static void main(String[] args) {
        A a = new A();
        a.hi();
        System.out.println(a.n1);

    }
}
//1.Deprecated 修饰某个元素，表示该元素已经过时
//2.即不再推荐使用，但是仍然可以使用
//3.查看 @Deprecated 注解类的源码
//4.可以修饰方法，类，字段，包，参数 等等
//5.@Deprecated可以做版本升级 过渡使用
/*
@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(value={CONSTRUCTOR, FIELD, LOCAL_VARIABLE, METHOD, PACKAGE, PARAMETER, TYPE})
public @interface Deprecated {
}

 */
@Deprecated
class A{
    @Deprecated
    public int n1=10;
    @Deprecated
    public void hi(){

    }
}

```

## collection_

![1625472023110](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\1625472023110.png)

### Collection_

```java
package com.study.collection_;

import java.util.ArrayList;
import java.util.Collection;
import java.util.HashMap;
import java.util.Map;
@SuppressWarnings({"all"})
public class Collection_ {
    public static void main(String[] args) {
        //1.集合主要是两组(单例集合，双列集合)
        //2.Collection 接口有两个重要的子接口 List Set ，他们的实现子类是单列集合
        //3.Map 接口的实现子类 是双列集合，存放的K-V
        ArrayList arrayList=new ArrayList();
        arrayList.add("Jack");
        arrayList.add("tom");

        HashMap hashMap=new HashMap();
        hashMap.put("NO1","北京");
        hashMap.put("NO2","上海");


    }
}

```

### CollectionMethod

```java
package com.study.collection_;

import java.util.ArrayList;
import java.util.List;
@SuppressWarnings({"all"})
public class CollectionMethod {
    public static void main(String[] args) {
        List list = new ArrayList();
        //add添加单个元素
        list.add("Jack");
        list.add(10);
        list.add(true);
        System.out.println("list="+list);
        //remove 删除指定元素
        list.remove(0);//删除第一个元素
        list.remove(true);//指定删除某个元素
        System.out.println("list="+list);
        //contains查找某个元素
        System.out.println(list.contains("Jack"));//F
        //size获取某个元素
        System.out.println(list.size());//1
        //isEmpty判断是否为空
        System.out.println(list.isEmpty());//F
        //clear清空
        list.clear();
        System.out.println("list="+list);
        //addAll 添加多个元素
        ArrayList list2 = new ArrayList();
        list2.add("红楼梦");
        list2.add("三国演义");
        list.addAll(list2);
        System.out.println("list="+list);
        //containsAll查找多个元素 是否存在
        System.out.println(list.containsAll(list2));//T
        //remove删除多个元素
        list.add("聊斋");
        list.removeAll(list2);
        System.out.println("list="+list);







    }
}

```

### CollectionIterator

```java
package com.study.collection_;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Comparator;
import java.util.Iterator;

public class CollectionIterator {
    public static void main(String[] args) {

       Collection col = new ArrayList();
       col.add(new Book("三国演义","罗贯中",10.1));
       col.add(new Book("小李飞刀","古龙",5.1));
       col.add(new Book("红楼梦","曹雪芹",34.6));
        //System.out.println("col="+col);
        //希望遍历集合
        //1.先得到 col 对应的 迭代器
        Iterator iterator= col.iterator();
        //2.使用while循环遍历即可
        while (iterator.hasNext()) {//判断是否还有数据
            //返回下一个元素   类型是obj
            Object obj = iterator.next();
            System.out.println("obj=" + obj);

        }
            //快捷键 itit 回车
            //显示所有快捷键ctrl+J
            //3.当迭代器退出while循环后，这时iterator迭代器，指向最后的元素
            //iterator.next();//NoSuchElementException
            //如果希望再次遍历 需要重置我们的迭代器
            iterator=col.iterator();
        System.out.println("====第二次遍历====");
        while (iterator.hasNext()) {
            Object obj= iterator.next();
            System.out.println("obj="+obj);
        }







    }
}
class Book{
    private String name;
    private String author;
    private double price;

    public Book(String name, String author, double price) {
        this.name = name;
        this.author = author;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getAuthor() {
        return author;
    }

    public void setAuthor(String author) {
        this.author = author;
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
                ", author='" + author + '\'' +
                ", price=" + price +
                '}';
    }
}
```

### CollectionFor

```java
package com.study.collection_;

import java.util.ArrayList;
import java.util.Collection;

public class CollectionFor {
    @SuppressWarnings({"all"})
    public static void main(String[] args) {

        Collection col = new ArrayList();

        col.add(new Book("三国演义","罗贯中",10.1));
        col.add(new Book("小李飞刀","古龙",5.1));
        col.add(new Book("红楼梦","曹雪芹",34.6));


        //1.使用增强for循环 在Collection集合
        //2.增强for，底层仍然是迭代器
        //3.增强for可以理解成就是简化版本的迭代器 遍历
        //4.快捷键 I

        for (Object book:col){
            System.out.println("book="+book);
        }

    }
}

```

### CollectionExercise

```java
package com.study.collection_;

import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

public class CollectionExercise {
    public static void main(String[] args) {
        Collection col = new ArrayList();
        col.add(new Dog("小黄",10));
        col.add(new Dog("小花",9));
        Iterator iterator=col.iterator();
        while (iterator.hasNext()) {
            Object dog =  iterator.next();
            System.out.println("dog="+dog);

        }
        for (Object o :col) {
            System.out.println("Dog="+o);

        }


    }
}
class Dog{
    private String name;
    private int age;

    public Dog(String name, int age) {
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

    @Override
    public String toString() {
        return "Dog{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

### ArrayListDetail

```java
package com.study.collection_;

import java.lang.reflect.Array;
import java.util.ArrayList;

@SuppressWarnings({"all"})
public class ArrayListDetail {
    public static void main(String[] args) {

        //ArrayList是由数组来实现数据存储的
        //ArrayList时线程不安全的(执行效率高)，可以看源码 没有这个synchronized
        /*
         public boolean add(E e) {
              ensureCapacityInternal(size + 1);  // Increments modCount!!
              elementData[size++] = e;
              return true;
    }
         */
        ArrayList arrayList = new ArrayList();
        arrayList.add(null);
        arrayList.add("Jack");
        arrayList.add(null);
        System.out.println(arrayList);
    }
}

```

### ArrayListSource

```java
package com.study.collection_;

import java.util.ArrayList;

@SuppressWarnings({"all"})
public class ArrayListSource {
    /*
    （2）当创建ArrayList对象时，如果使用的是无参构造器，则初始elementData容量为0，
    第一次添加，则扩容elementData为10，如果需再次扩容，则扩容elementData为1.5倍

     */
    public static void main(String[] args) {
        //使用无参构造器创建ArrayList对象
        /*1.创建了一个空的elementData数组={}
        public ArrayList() {
        this.elementData = DEFAULTCAPACITY_EMPTY_ELEMENTDATA;
    }
        //2.执行list.add（1）先确定是否要扩容 （2）然后在执行 赋值
         public boolean add(E e) {
        ensureCapacityInternal(size + 1);  // Increments modCount!!
        elementData[size++] = e;
        return true;
    }

       //3.该方法确定minCapacity (1)第一次扩容  为10
       private void ensureCapacityInternal(int minCapacity) {
        ensureExplicitCapacity(calculateCapacity(elementData, minCapacity));
    }
       //4.
       private void ensureExplicitCapacity(int minCapacity) {
             modCount++;//（1）记录集和修改的次数

             // overflow-conscious code
              if (minCapacity - elementData.length > 0)
                  grow(minCapacity);（2)如果elementData大小不够，就调用grow()去扩容
          }

          //5.private void grow(int minCapacity) {                          //（1）真的扩容
          //        // overflow-conscious code                              //（2）使用扩容机制确定要扩容到多大
          //        int oldCapacity = elementData.length;                   //（3）第一次newCapacity=10
          //        int newCapacity = oldCapacity + (oldCapacity >> 1);     //（4）第二次及其以后，按照1.5倍扩容
          //        if (newCapacity - minCapacity < 0)                      //（5）扩容使用的是Arrays.copyOf() 会保留原有的数据
          //            newCapacity = minCapacity;
          //        if (newCapacity - MAX_ARRAY_SIZE > 0)
          //            newCapacity = hugeCapacity(minCapacity);
          //        // minCapacity is usually close to size, so this is a win:
          //        elementData = Arrays.copyOf(elementData, newCapacity);
          //    }


         */
        /*
        如果使用的是指定大小的构造器，则初始elementData容量为指定大小，
        如果需要扩容，则直接扩容elementData为1.5倍
         */

        ArrayList list = new ArrayList();


        //使用for循环给list集合添加 1-10数据
        for (int i = 1; i <=10; i++) {
            list.add(i);
            
        }
        //使用for循环给list集合添加 11-15数据
        for (int i = 11; i <=15; i++) {
            list.add(i);

        }


        list.add(100);
        list.add(200);
        list.add(null);



    }
}

```

## list_

### List_

```java
package com.study.list_;

import java.util.ArrayList;

public class List_ {
    @SuppressWarnings({"all"})
    public static void main(String[] args) {
        //List集合类中元素有序（即添加顺序和取出顺序一致、且可重复【案列】）
        ArrayList list = new ArrayList();
        list.add("Tom");
        list.add("Jack");
        list.add("Mary");
        list.add("Tom");
        System.out.println("list="+list);
        //2.List集合中的每个元素都有其对应的顺序索引，即支持索引
        //索引是从0开始的
        System.out.println(list.get(2));
        //3.

    }
}

```

### ListMethod

```java
package com.study.list_;

import java.util.ArrayList;
import java.util.List;

public class ListMethod {
    @SuppressWarnings({"all"})
    public static void main(String[] args) {
        List list = new ArrayList();
        list.add("张三丰");
        list.add("贾宝玉");
        //1.void add(int index,Object ele):在index位置插入ele元素
        list.add(1,"冯");
        System.out.println("list="+list);
        //2.boolean addAll(int index,Collection eles):从index位置开始将eles中的所有元素添加进来
        List list2=new ArrayList();
        list2.add("tom");
        list2.add("Jack");
        list2.add("tom");
        list.addAll(1,list2);
        //3.get(int index):获取指定index位置的元素
        //4.indexOf(Object obj) 返回obj在当前集合中首次出现的位置
        System.out.println("list="+list);
        System.out.println(list.indexOf("tom"));
        //5.lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置
        System.out.println("list="+list);
        System.out.println(list.lastIndexOf("tom"));
        //6.remove(int index):移除指定index位置的元素，并返回元素
        list.remove(0);
        System.out.println("list="+list);
        //7.Object set(int index,Object eles):设置指定index位置的元素为ele，相当于是替换
        list.set(1,"玛丽");//索引必须存在 否则报错
        System.out.println("list="+list);
        //8.List subList(int fromIndex,int toIndex):返回从fromIndex到toIndex位置的子集合
        //注意：返回的子集合 formIndex<=subList<toIndex 左闭右开
        List returnlist=list.subList(0,2);
        System.out.println("returnList"+returnlist);






    }
}

```

### ListFor

```java
package com.study.list_;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class ListFor {
    public static void main(String[] args) {
        //List接口的实现子类 Vector LinkedList 运行类型完全OK
        List list = new ArrayList();

        list.add("jack");
        list.add("tom");
        list.add("鱼香肉丝");
        list.add("北京烤鸭");

        //遍历
        //1.迭代器
        Iterator iterator=list.iterator();
        while (iterator.hasNext()) {
            Object obj = iterator.next();
            System.out.println("obj="+obj);
        }

        System.out.println("=======增强for循环========");
        //2.增强for循环
        for (Object o :list) {
            System.out.println("o="+o);

        }
        System.out.println("=======普通for循环========");
        //3.使用普通for循环
        for (int i = 0; i < list.size(); i++) {
            System.out.println("对象="+list.get(i));
            
        }

    }
}

```

### ListExercise

```java
package com.study.list_;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class ListExercise {
    public static void main(String[] args) {
        /*
        添加10个以上的元素（比如String “hello"),在2号位插入一个元素"韩顺平教育"
        获得第5个元素，删除第6个元素，修改第7个元素，在使用迭代器遍历集合
        要求：使用List的实现类ArrayList完成。
         */
        List list = new ArrayList();
        for (int i = 0; i < 12; i++) {
            list.add("hello"+i);
            
        }
        System.out.println("list="+list);
        //在2号位插入一个元素："韩顺平教育"
        list.add(1,"韩顺平教育");
        System.out.println("list="+list);
        //获得第5个元素
        System.out.println("第五个元素="+list.get(4));
        //删除第6个元素
        list.remove(5);
        System.out.println("list="+list);
        //修改第7个元素
        list.set(6,"三国演义");
        System.out.println("list="+list);
        //使用迭代器遍历
        Iterator iterator=list.iterator();
        while (iterator.hasNext()) {
            Object obj = iterator.next();
            System.out.println("obj="+obj);

        }

    }
}

```

### ListExercise02

```java
package com.study.list_;

import java.util.ArrayList;
import java.util.List;

public class ListExercise02 {
    @SuppressWarnings({"all"})
    public static void main(String[] args) {
        List list = new ArrayList();

        list.add(new Book("红楼梦","曹雪芹",100));
        list.add(new Book("西游记","吴承恩",10));
        list.add(new Book("水浒传","施耐庵",19));
        list.add(new Book("三国","曹雪芹",80));
       // list.add(new Book("西游记","曹雪芹",10));


        //遍历
        for (Object o :list) {
            System.out.println(o);

        }
        sort(list);
        System.out.println("===排序后===");
        for (Object o :list) {
            System.out.println(o);

        }


    }
    //价格要求从小到大
    public static void sort(List list){
        int listSize= list.size();
        for (int i = 0; i < listSize-1; i++) {
            for (int j = 0; j < listSize-1-i; j++) {
                //取出对象Book
                Book book1=(Book)list.get(j);
                Book book2=(Book)list.get(j+1);
                if(book1.getPrice()>book2.getPrice()){//交换
                    list.set(j,book2);
                    list.set(j+1,book1);

                }
                
            }
            
        }
    }
}
class Book{
    private String name;
    private String author;
    private double price;

    public Book(String name, String author, double price) {
        this.name = name;
        this.author = author;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getAuthor() {
        return author;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    @Override
    public String toString() {
        return "名称:"+name+"\t\t价格:"+price+"\t\t作者:"+author;
    }
}
```

### LinkedList01

```java
package com.study.list_;

public class LinkedList01 {
    public static void main(String[] args) {
        //模拟一个简单的双向链表
        Node jack = new Node("Jack");
        Node tom = new Node("Tom");
        Node frx = new Node("Frx");

        //链接三个结点，形成双向链表
        //jack->Tom->frx
        jack.next=tom;
        tom.next=frx;
        //frx->Tom->jack
        frx.pre=tom;
        tom.pre=jack;

        Node first=jack;//让first引用指向jack，就是双向链表的头结点
        Node last=frx;//让last引用指向hsp，就是双向链表的尾结点

        //演示从头到尾进行遍历
        System.out.println("===从头到尾进行遍历===");
        while(true){
            if(first==null){
                break;
            }
            //输出first信息
            System.out.println(first);
            first=first.next;
        }
        //添加一个数据
        //要求在 tom和frx 插入一个对象 smith

        //1.先创建一个Node 结点
        Node smith = new Node("Smith");
        //下面就把Smith加入双向链表
        smith.next=frx;
        smith.pre=tom;
        frx.pre=smith;
        tom.next=smith;

        //让first再次指向jack
        first=jack;

        System.out.println("===从头到尾进行遍历===");
        while(true){
            if(first==null){
                break;
            }
            //输出first信息
            System.out.println(first);
            first=first.next;
        }

    }
}
//定义一个Node类，Node对象 表示双向链表的一个结点
class Node{
    public Object item;//真正存放数据
    public Node next;//指向后一个结点
    public Node pre;//指向前一个结点
    public Node(Object name){
        this.item=name;
    }

    @Override
    public String toString() {
        return "Node{" +
                "name=" + item +
                '}';
    }
}
```

### LinkedListCRUD

```java
package com.study.list_;

import java.util.Iterator;
import java.util.LinkedList;
@SuppressWarnings({"all"})
public class LinkedListCRUD {
    public static void main(String[] args) {

        LinkedList linkedList = new LinkedList();
        linkedList.add(1);
        linkedList.add(2);
        linkedList.add(3);
    System.out.println("liskedList="+linkedList);
    //演示删除结点的源码
        linkedList.remove();//默认删除第一个结点
        //linkedList.remove(2);

        System.out.println("liskedList="+linkedList);
        //修改某个结点对象
        linkedList.set(1,999);
        System.out.println("liskedList="+linkedList);

        //得到某个结点对象
        //get(1) 是得到双向链表的第二个对象
        Object o=linkedList.get(1);
        System.out.println(o);

        //因为LinkedList 是实现List接口，遍历方式
        System.out.println("==========LinkedList遍历迭代器=============");
        Iterator iterator = linkedList.iterator();
        while (iterator.hasNext()) {
            Object next =  iterator.next();
            System.out.println("next="+next);
            
        }
        for (Object o1 :linkedList) {
            System.out.println("o1="+o1);
        }


        //源码阅读
        //1.LinkedList linkedList = new LinkedList();
         /*public LinkedList() {
        }
        //2.这时linkedlist 的属性 first=null last=null
        3.执行
         public boolean add(E e) {
            linkLast(e);
            return true;
        }
        //4. 将新的结点，加入到我们的双向链表的最后
         void linkLast(E e) {
        //        final Node<E> l = last;
        //        final Node<E> newNode = new Node<>(l, e, null);
        //        last = newNode;
        //        if (l == null)
        //            first = newNode;
        //        else
        //            l.next = newNode;
        //        size++;
        //        modCount++;
        //    }

*/      /*
            1.执行 removeFirst();
            public E remove() {
                    return removeFirst();
                }
                2.public E removeFirst() {
                    final Node<E> f = first;
                    if (f == null)
                        throw new NoSuchElementException();
                    return unlinkFirst(f);
                }
                3.执行unlinkFirst，将f 指向双向链表的第一个结点
                private E unlinkFirst(Node<E> f) {
                    // assert f == first && f != null;
                    final E element = f.item;
                    final Node<E> next = f.next;
                    f.item = null;
                    f.next = null; // help GC
                    first = next;
                    if (next == null)
                        last = null;
                    else
                        next.prev = null;
                    size--;
                    modCount++;
                    return element;
                }



*/
    }
}
//如何选择ArrayList和LinkedList:
//1.如果我们改查的操作多，先择ArrayList 线程不安全 尽量单线程
//2.如果我们增删的操作多，选择LinkedList  线程不安全 尽量单线程
//3.一般来说，在程序中，80%~90%都是查询，因此大部分情况下会选择ArrayList
//4.在一个项目中，根据业务灵活选择，也可能这样，一个模块使用的是ArrayList，
//另外一个模块是LinkedList
```

### Vector_

```java
package com.study.list_;

import java.util.Vector;

@SuppressWarnings({"all"})
public class Vector_ {
    public static void main(String[] args) {
        //无参构造器
        Vector vector = new Vector();
        for (int i = 0; i < 10; i++) {
            vector.add(i);
            
        }
        vector.add(100);
        System.out.println("Vector="+vector);
        //解读源码
        //1.new Vector() 底层
        /* public Vector() {
               this(10);
          }
          补充:如果是 Vector vector=new Vector(8);
          走的方法：
          public Vector(int initialCapacity) {
                this(initialCapacity, 0);
            }

            2.vector.add(i)
          2.1//下面这个方法就是添加数据到Vector集合
           public synchronized boolean add(E e) {
               modCount++;
               ensureCapacityHelper(elementCount + 1);
               elementData[elementCount++] = e;
               return true;
    }
         2.2//确定是否需要扩容条件：minCapacity-elementDate.length>0
         private void ensureCapacityHelper(int minCapacity) {
        // overflow-conscious code
        if (minCapacity - elementData.length > 0)
            grow(minCapacity);
    }
       2.3 //如果 需要的数组大小不够用，就扩容，扩容后的算法
        private void grow(int minCapacity) {
        // overflow-conscious code
        int oldCapacity = elementData.length;
        int newCapacity = oldCapacity + ((capacityIncrement > 0) ?
                                         capacityIncrement : oldCapacity);
          //就是扩容两倍
        if (newCapacity - minCapacity < 0)
            newCapacity = minCapacity;
        if (newCapacity - MAX_ARRAY_SIZE > 0)
            newCapacity = hugeCapacity(minCapacity);
        elementData = Arrays.copyOf(elementData, newCapacity);
    }
          */


    }
}

```

## hashset_

### SetMethod

```java
package com.study.set_;

import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

@SuppressWarnings({"all"})
public class SetMethod {
    public static void main(String[] args) {

        //1.以Set接口 的实现类 HashSet 来讲解 Set 接口的方法
        //2.set接口的实现类的对象（Set接口对象)，不能存放重复的元素，可以添加一个null
        //3.set接口对象存放数据是无序(即添加的顺序和取出的顺序不一致)
        //4.注意：取出的顺序虽然不是添加的顺序，但是它是固定的
       Set set = new HashSet();
       set.add("john");
       set.add("lucy");
       set.add("john");//重复的数据
       set.add("jack");
       set.add("john");
       set.add("frx");
       set.add(null);
       set.add(null);

       set.remove(null);

        System.out.println("set="+set);



        //遍历
        //方式一：使用迭代器
        System.out.println("=====使用迭代器遍历======");
        Iterator iterator = set.iterator();
        while (iterator.hasNext()) {
            Object obj = iterator.next();
            System.out.println("obj="+obj);
        }


        //方式二：增强for循环
        System.out.println("=======增强for循环=======");

        for (Object o :set) {
            System.out.println("o="+o);

        }
        //set 接口对象 不能通过索引来获取

    }
}

```



### Hashset_

```java
package com.study.set_;

import java.util.HashSet;
import java.util.Set;

public class Hashset_ {
    public static void main(String[] args) {
        Set hashSet = new HashSet();
        hashSet.add(null);
        hashSet.add(null);
        System.out.println("hashset="+hashSet);


        /*
        1.  public HashSet() {
              map = new HashMap<>();
    }
        2.  hashset可以存放null，但是只能有一个null 即元素不能重复


         */
    }
}

```

### Hashset01

```java
package com.study.set_;

import java.util.HashSet;
import java.util.Set;
@SuppressWarnings({"all"})
public class Hashset01 {
    public static void main(String[] args) {
        HashSet set = new HashSet();


        //说明：
        //1.在执行add方法后，会返回一个boolean值
        //2.如果添加成功，返回true，否则返回false
        //3.可以通过remove指定删除某个对象
       System.out.println(set.add("john"));//T
        System.out.println(set.add("lucy"));//T
        System.out.println(set.add("john"));//F
        System.out.println(set.add("jack"));//T
        System.out.println(set.add("Rose"));//T



        set.remove("john");
        System.out.println("set="+set);//3个


        //
        set=new HashSet();
        System.out.println("set="+set);//0个
        //Hashset 不能添加相同的元素/数据
        set.add("lucy");//添加成功
        set.add("lucy");//加入不了
        set.add(new Dog("tom"));
        set.add(new Dog("tom"));//两个不同的对象
        System.out.println("set="+set);


        //看源码
        set.add(new String("frx"));//ok
        set.add(new String("frx"));//加入不了


    }
}
class Dog{//定义了Dog类
    private String name;

    public Dog(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "Dog{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

### HashsetStructure

```java
package com.study.set_;
@SuppressWarnings({"all"})
public class HashsetStructure {
    public static void main(String[] args) {
        //模拟一个 HashSet的底层 （HashMap的底层结构）

        //1.创建一个数组，数组类型是 Node[]
        //2.有些人，直接把 Node[] 数组称为表

        Node[] table=new Node[16];
        System.out.println("table="+table);
        //3.创建结点，
        Node john = new Node("john", null);

        table[2]=john;
        Node jack = new Node("jack", null);
        john.next=jack;//将jack结点挂载到john

        Node rose = new Node("Rose", null);
        jack.next=rose;//将rose 结点挂载到 jack

        Node luck=new Node("luck",null);
        table[3]=luck;//把 luck反到 table表的索引为3
        System.out.println("table="+table);


    }
}
class Node{//结点，存储数据可以指向下一个结点，从而形成链表
    Object item;//存放数据
    Node next;//可以指向下一个结点

    public Node(Object item, Node next) {
        this.item = item;
        this.next = next;
    }
}
```

### HashsetSource

```java
package com.study.set_;

import java.util.HashSet;

@SuppressWarnings({"all"})
public class HashsetSource {
    public static void main(String[] args) {

        HashSet hashSet = new HashSet();
        hashSet.add("java");
        hashSet.add("php");
        hashSet.add("java");
        System.out.println("set="+hashSet);

        /*
        源码解读：
        1.执行Hashset
        public HashSet() {
            map = new HashMap<>();
    }
        2.执行add()
         public boolean add(E e) {
            return map.put(e, PRESENT)==null; //PRESENT=new Object();
          }
        3.执行put方法 该方法会执行hash(key) 得到key对应的hash值 算法是h = key.hashCode()) ^ (h >>> 16)
         public V put(K key, V value) {  //key 是java
            return putVal(hash(key), key, value, false, true);
    }
        4.执行 putVal
        final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                   boolean evict) {
        Node<K,V>[] tab; Node<K,V> p; int n, i;//定义了辅助变量
        //table 就是HashMap 的一个数组，类型是 Node[]
        // if语句 表示如果当前table 是null，或者大小==0
        //就是第一次扩容，到16个空间
        if ((tab = table) == null || (n = tab.length) == 0)
            n = (tab = resize()).length;
        //(1)根据key得到的hash 去计算该key应该存放在table表的哪个索引位置
        //并把这个位置的对象， 赋给 p
        //(2)判断p是否为null
        //(2.1) 如果 p为null，表示没有存放过元素，就创建一个Node(key="java",value=PRESENT)
        //(2.2)就放在该位置 tab[i]=newNode(hash, key, value, null)

        if (p = tab[i = (n - 1) & hash]) == null)
            tab[i] = newNode(hash, key, value, null);
        else {
        //一个开发技巧提示：在需要局部变量（辅助变量）时候，在创建
            Node<K,V> e; K k;//
            //如果当前索引位置对应的链表的第一个元素和准备添加的key的 hash值一样
            //并且满足下面两个条件之一：
             //(1)准备加入的 key和p指向的 Node结点的key 是同一个对象
             //(2)或者p指向的 Node结点的key 的equals() 和准备加入的key比较后 相同
             //就不能加入
            if (p.hash == hash &&
                ((k = p.key) == key || (key != null && key.equals(k))))
                e = p;
              //再判断 p是不是一颗红黑树，
              //如果是一颗红黑树，就调用 putTreeVal() 来进行添加
            else if (p instanceof TreeNode)
                e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
            else {//如果table对应索引位置，已经是一个链表，就使用for循环比较
            //(1)依次和该链表的每一个元素比较后，都不相同，则加入到该链表的最后
            //   注意再把元素添加到链表后，立即判断 该链表是否已经达到8个结点
            //   就调用 treeifyBin() 对当前这个链表进行树化(转成红黑树)
            //   注意，再转成红黑树时，要进行判断， 判断条件如下：
            //       if (tab == null || (n = tab.length) < MIN_TREEIFY_CAPACITY)
            //          resize();
            //如果上面条件成立，先table扩容
            // 只有上面条件不成立时，才转换成红黑树
            //(2)次和该链表的每一个元素比较过程中，如果有相同的情况，就直接break

                for (int binCount = 0; ; ++binCount) {
                    if ((e = p.next) == null) {
                        p.next = newNode(hash, key, value, null);
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k))))
                        break;
                    p = e;
                }
            }
            if (e != null) { // existing mapping for key
                V oldValue = e.value;
                if (!onlyIfAbsent || oldValue == null)
                    e.value = value;
                afterNodeAccess(e);
                return oldValue;
            }
        }
        ++modCount;
        //size 就是我们每加入一个结点Node(k,v,h,next) ,size就会加加
        if (++size > threshold)
            resize();//扩容
        afterNodeInsertion(evict);
        return null;
    }

         */

    }
}
/*
1.HashSet 底层是HashMap
2.添加一个元素时，先得到hash值，会转成->索引值
3.找到存储数据表table，看这个索引位置是否已经存放的有元素
4.如果没有，直接加入
5.如果有，调用 equals比较，如果相同，就放弃添加，如果不相同，则添加到最后
6.在java8中，如果一条链表的元素个数到达 TREEIFY_THRESHOLD(默认64) 就会进行树化（红黑树）
 */
```

### HashSetIncrement

```java
package com.study.set_;

import java.util.HashSet;
import java.util.Objects;

@SuppressWarnings({"all"})
public class HashSetIncrement {
    public static void main(String[] args) {
        /*
        HashSet底层是HashMap，第一次添加时，table数组扩容到 16，
        临界值(threshold)是 16*加载因子(loadFactor)是0.75=12
        如果table 数组使用到了临界值 12，就会扩容到 16*2=32，
        新的临界值就是 32*0.75=24，依次类推
         */

       HashSet hashSet = new HashSet();
       /* for (int i = 1; i <=100; i++) {
            hashSet.add(i);

        }
*/
        /*
        在java8中，如果一条链表的元素个数达到 TREEIFY_THRESHOLD（默认是 8),
        并且table的大小 >=MIN_TREEIFY_THRESHOLD（默认是 64),就会进行树化(红黑树),
        否则仍然采用数组扩容机制
         */
//        for (int i = 1; i <= 12; i++) {
//            hashSet.add(new A(i));//
//        }
//        System.out.println("hashset="+hashSet);

        /*
        当我们hashset增加一个元素，->Node->加入table，就算是增加了一个size++
         */

        for (int i = 1; i <=7; i++) {//在table的某一条链表上添加了7个A对象
            hashSet.add(new A(i));

        }
        for (int i = 1; i <=7; i++) {//在table的另外一条链表上添加了7个B对象
            hashSet.add(new B(i));

        }
    }
}
class B{
    private int n;

    public B(int n) {
        this.n = n;
    }


    @Override
    public int hashCode() {
        return 200;
    }
}
class A{
    private int n;

    public A(int n) {
        this.n = n;
    }

    @Override
    public int hashCode() {
        return 100;
    }
}
```

### HashSetExercise

```java
package com.study.set_;

import java.util.HashSet;
import java.util.Objects;

public class HashSetExercise {
    public static void main(String[] args) {
        /**
        定义一个Employee类，该类包含：private成员属性name，age 要求：
         创建3个Employee 对象放入HashSet中
         当name和age的值相同时，认为是相同员工，不能添加到HashSet集合中
         */
        HashSet hashSet = new HashSet();
        hashSet.add(new Employee("milan",18));
        hashSet.add(new Employee("smith",28));
        hashSet.add(new Employee("milan",18));


        System.out.println("hashSet="+hashSet);
    }
}
class Employee{
    private String name;
    private int age;

    public Employee(String name, int age) {
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

    @Override
    public String toString() {
        return "Employee{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
    //如果name 和 age 值相同，则返回相同的hash值

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Employee employee = (Employee) o;
        return age == employee.age && Objects.equals(name, employee.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }
}
```

### HashSetExercise02

```java
package com.study.set_;

import java.util.HashSet;
import java.util.Objects;
@SuppressWarnings({"all"})
/**
 * 定义一个Employee类，该类包含：private成员属性name，salbirthday(MyDate类型),
 * 其中birthday为Mydate类型(属性包括:year,month,day),要求：
 * 1.创建3个Employee 放入HashSet中
 * 2.当name和birthday的值相同时，认为是相同员工，不能添加到HashSet集合中
 */
public class HashSetExercise02 {
    public static void main(String[] args) {
        HashSet hashSet = new HashSet();
        hashSet.add(new Employee1("frx",10.0,new MyDate(2001,1,1)));
        hashSet.add(new Employee1("frx",20.0,new MyDate(2001,1,1)));
        hashSet.add(new Employee1("milan",20.0,new MyDate(2001,1,1)));
        System.out.println("employer="+hashSet);


    }
}
class Employee1 {
    private String name;
    private double sal;
    private MyDate birthday;

    public Employee1(String name, double sal, MyDate birthday) {
        this.name = name;
        this.sal = sal;
        this.birthday = birthday;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getSal() {
        return sal;
    }

    public void setSal(double sal) {
        this.sal = sal;
    }

    public MyDate getBirthday() {
        return birthday;
    }

    public void setBirthday(MyDate birthday) {
        this.birthday = birthday;
    }

    @Override
    public String toString() {
        return "Employee1{" +
                "name='" + name + '\'' +
                ", sal=" + sal + "," +
                birthday +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Employee1 employee1 = (Employee1) o;
        return Objects.equals(name, employee1.name) && Objects.equals(birthday, employee1.birthday);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, birthday);
    }
}
class MyDate{
    private int year;
    private int month;
    private int day;

    public MyDate(int year, int month, int day) {
        this.year = year;
        this.month = month;
        this.day = day;
    }

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        this.year = year;
    }

    public int getMonth() {
        return month;
    }

    public void setMonth(int month) {
        this.month = month;
    }

    public int getDay() {
        return day;
    }

    public void setDay(int day) {
        this.day = day;
    }

    @Override
    public String toString() {
        return "MyDate{" +
                "year=" + year +
                ", month=" + month +
                ", day=" + day +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        MyDate myDate = (MyDate) o;
        return year == myDate.year && month == myDate.month && day == myDate.day;
    }

    @Override
    public int hashCode() {
        return Objects.hash(year, month, day);
    }
}
```

### LinkedHashSetSource

```java
package com.study.set_;

import java.util.LinkedHashMap;
import java.util.LinkedHashSet;
import java.util.Set;

/**
 * @author frx
 * @version 1.0
 * @date 2021/7/5  15:00
 */
public class LinkedHashSetSource {
    public static void main(String[] args) {
        //分析LinkedHashSet的底层机制
        Set set = new LinkedHashSet();
        set.add(new String("AA"));
        set.add(456);
        set.add(456);
        set.add(new Customer("冯",1001));
        set.add(123);
        set.add("frx");

        System.out.println("set="+set);
        //1.LinkedHashSet 加入顺序和取出元素/数据的顺序一致
        //2.LinkedHashSet 底层维护的是一个LinkedHashMap(是HashMap)的子类
        //3.LinkedHashSet 底层结构(数组+双向链表)
        //4.添加第一次时，直接将数组table 扩容到16,存放的节点类型是LinkedHashMap$Entry
        //5.数组是 HashMap$Node[] 存放的元素/数据是 LinkedHashMap$Entry类型
        /*
        //继承关系是在内部类完成，
         static class Entry<K,V> extends HashMap.Node<K,V> {
            Entry<K,V> before, after;
            Entry(int hash, K key, V value, Node<K,V> next) {
                super(hash, key, value, next);
            }
    }
         */
    }


}
class Customer{
    String name;
    int tell;

    public Customer(String name, int tell) {
        this.name = name;
        this.tell = tell;
    }
}
```

### LinkedHashSetExercise

```java
package com.study.set_;

import java.util.LinkedHashSet;
import java.util.Objects;

/**
 * @author frx
 * @version 1.0
 * @date 2021/7/5  15:42
 */
@SuppressWarnings({"all"})
public class LinkedHashSetExercise {
    public static void main(String[] args) {
        LinkedHashSet linkedHashSet = new LinkedHashSet();
        linkedHashSet.add(new Car("奥拓",1000));
        linkedHashSet.add(new Car("奥迪",300000));
        linkedHashSet.add(new Car("法拉利",10000000));
        linkedHashSet.add(new Car("奥迪",300000));
        linkedHashSet.add(new Car("保时捷",70000000));
        linkedHashSet.add(new Car("奥迪",300000));

        System.out.println("linkedHashSet="+linkedHashSet);


    }
}

/**
 * Car 类（属性：name ,price) 如果name和 price一样
 * 则认为是相同元素，就不能添加
 */
class Car{
    private String name;
    private double price;

    public Car(String name, double price) {
        this.name = name;
        this.price = price;
    }

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
        return "\nCar{" +
                "name='" + name + '\'' +
                ", price=" + price +
                '}';
    }
    //重写equals方法 和hashCode
    //当name和 price相同时，就返回相同的 hashCode值，equals 返回true

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Car car = (Car) o;
        return Double.compare(car.price, price) == 0 && Objects.equals(name, car.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, price);
    }
}
```

