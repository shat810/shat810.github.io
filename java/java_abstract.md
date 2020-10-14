# java 抽象类
Java抽象方法是指没有执行语句的方法`public void run(){}`

可以用abstract修饰`public abstract void run()`这样就声明了一个抽象方法。抽象方法因为没有任何的执行语句，所以无法编译。
```java
class Person{
    public abstract void run()
}
```
由此Person类也无法实例化，所以我们把Person类声明为抽象类
```java
abstract class Person{
    public abstract void run()
}
```
这就是一个抽象类，抽象类无法被实例化，所以抽象类只能被继承，当他被继承时，就可以强制子类，重写他的抽象方法，这也在一定程度上定义了规范。
```java
 class Student extends Person{
    public void run(){
        System.out.println("Student.run");
    }
}
```
我们一般使用抽象类去实例化子类`Person s = new Student();`然后使用`s.run();`就可以不考虑子类的具体类型。这就是面向抽象编程的思想。
