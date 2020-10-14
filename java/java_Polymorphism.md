# java多态
要理解多态首先要了解多态的前提，首先需要子类继承父类，然后子类要覆写父类的方法，最后必须父类引用指向子类的方法类型。
```java
public class Main {
    public static void main(String[] args) {
        Person p = new Student();
        p.run(); // 应该打印Person.run还是Student.run?
    }
}

class Person {
    public void run() {
        System.out.println("Person.run");
    }
}

class Student extends Person {
    @Override
    public void run() {
        System.out.println("Student.run");
    }
}
```
实际运行结果为`Student.run`这就是多态的体现。
运行期才能动态决定调用的子类方法。对某个类型调用某个方法，执行的实际方法可能是某个子类的覆写方法。
