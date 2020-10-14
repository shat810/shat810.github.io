# java 静态字段和静态方法
在Java中所有实例字段都有自己的独立的“空间”，互相不影响。但是静态字段共享一个“空间”。例如Person类中的number字段。
```java
public class Main {
    public static void main(String[] args) {
        Person ming = new Person("Xiao Ming", 12);
        Person hong = new Person("Xiao Hong", 15);
        ming.number = 88;
        System.out.println(hong.number);
        hong.number = 99;
        System.out.println(ming.number);
    }
}

class Person {
    public String name;
    public int age;

    public static int number;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```
输出结果为 88 99.任何一个实例化对象去改变静态字段的值都会把所有实例的静态字段改变了。

因为静态字段不属于字段，用实例化去引用它会自动转换为`Person class`的字段，所以正确的访问静态变量应该`Person.number`这样就不会造成误解。能把静态字段理解为类的字段，不是实例的字段。

## 静态方法
和静态字段一样用`static`修饰，同样使用类名来访问，因为静态方法无法实例化，所以不能使用this变量，也不能访问字段，只能访问静态字段。
```java
public class Main {
    public static void main(String[] args) {
        Person.setNumber(99);
        System.out.println(Person.number);
    }
}

class Person {
    public static int number;

    public static void setNumber(int value) {
        number = value;
    }
}
```

在接口中不能有字段，但是可以用静态字段，用`public static final`修饰。
```java
public interface Person {
    public static final int MALE = 1;
    public static final int FEMALE = 2;
}
```
