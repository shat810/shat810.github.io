# Java构造方法

在创建实例化对象时我们一般都会实例化他的字段。
```java
Person ming = new Person();
ming.setName("小明");
ming.setAge(12);
```
如果没有调用setName()或者setAge()，这个实例的内部状态就是不正确的。

我们可以利用构造方法就实例化对象的同时就实例化字段`Person ming = new Person("小明",12);` 我们一开始实例化对象的方法也是使用构造方法只是那个构造方法没有参数。
```java
public class Main {
    public static void main(String[] args) {
        Person p1 = new Person("Xiao Ming", 15); // 既可以调用带参数的构造方法
        Person p2 = new Person(); // 也可以调用无参数构造方法
    }
}

class Person {
    private String name;
    private int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public String getName() {
        return this.name;
    }

    public int getAge() {
        return this.age;
    }
}
```
构造方法的名字和类名一样，同时构成方法没有返回值，可以根据需要创建多个构造方法，在我们没有创建构造方法时，系统会自动帮我们创建一个没有参数的构造方法。`public Person(){}`

构造方法的调用系统会自动识别我们传递的参数个数和顺序，然后调用相应的构造方法。