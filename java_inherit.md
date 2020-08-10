# java继承
我们定义一个学生类
```java
class Student {
    private String name;
    private int age;
    private int score;

    public String getName() {...}
    public void setName(String name) {...}
    public int getAge() {...}
    public void setAge(int age) {...}
    public int getScore() { … }
    public void setScore(int score) { … }
}
```
他和Person类的区别不大只是多了一个score字段和getScore方法和setScore方法。这种时候我们为了提高代码的复用率就应该用继承。
```java
class Student extends Person{
    private int score;

    public int getScore() { … }
    public void setScore(int score) { … }
}
```
继承使得Student类获得了他的父类Person类的所有字段和方法，所以我们只需要定义Student类额外的功能就行了。

但是如果在父类中我们使用private修饰符的话，那么子类就无法调用父类的字段，我们继承的作用就没有用了。所以我们在父类中应该使用protected修饰符，这得以让父类的字段和方法能被子类和子类的子类访问。
```java
class Person {
    protected String name;
    protected int age;
}

class Student extends Person {
    public String hello() {
        return "Hello, " + name; // OK!
    }
}
```
在子类中访问父类的方法使用super关键词
```java
public class Main {
    public static void main(String[] args) {
        Student s = new Student("Xiao Ming", 12, 89);
    }
}

class Person {
    protected String name;
    protected int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

class Student extends Person {
    protected int score;

    public Student(String name, int age, int score) {
        super(name,age);
        this.score = score;
    }
}
```
我们可以看到使用super关键词就是访问了父类的构造方法。
在Java中，任何class的构造方法，第一行语句必须是调用父类的构造方法。如果没有明确地调用父类的构造方法，编译器会帮我们自动加一句`super();`

可以直接定义 `Person p = new Student();`这种向上转型的方法可以安全的把子类变成父类类型的赋值。

有向上转型就有向下转型,把父类的类型强行转换成子类类型就是向下转型。
```java
Person p1 = new Student();
Person p2 = new Person();
Student s1 = (Student)p1; //OK
Student s2 = (Student)p2; //runtime error! ClassCastException!
```
p2的类型是Person无法直接转化为Student类因为子类有父类的方法，但是父类没有子类额外的方法，p1本身类型就是Student所以能成功转换。

