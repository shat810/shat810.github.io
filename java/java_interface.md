# java接口
```java
abstract class Person {
    public abstract void run();
    public abstract String getName();
}
```
一个抽象类里面只有抽象方法没有字段，就可以把这个抽象类改写为接口。
```java
interface Person {
    void run();
    String getName();
}
```
我们都知道一个类只可以继承一个父类，但是可以接入多个接口
```java
interface Hello {
    void hello();
}
class Student implements Person,Hello {
    private String name;

    public Student(String name) {
        this.name = name;
    }

    @Override
    public void run() {
        System.out.println(this.name + " run");
    }

    @Override
    public String getName() {
        return this.name;
    }
}
```
接口还可以继承其他接口，例如:
```java
interface Person extends Hello{
    void run();
    String getName();
}
```
接口中可以加入一个default方法，这个方法不一定要被子类覆写。
