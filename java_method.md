# java 方法

在给对象的字段赋值的时候，因为外面传递的数据可能会造成逻辑混乱，所以使用方法在内部进行判断。

例如：`ming.age = - 99` 这很容易就造成逻辑混乱，我们在类内部把字段的修饰符设置成 private。
```java
class Person{
    private String name;
    private String sex;
    private int age;
}
```
这样外部代码就不能访问这些字段，我们使用方法来设置和获取这些字段
```java

public class Main {
    public static void main(String[] args) {
        Person ming = new Person();
        ming.setName("Xiao Ming"); // 设置name
        ming.setAge(12); // 设置age
        System.out.println(ming.getName() + ", " + ming.getAge());
    }
}

class Person{
    private String name;
    private int age;

    public String getName() {
        return this.name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return this.age;
    }

    public void setAge(int age) {
        if (age < 0 || age > 100) {
            throw new IllegalArgumentException("invalid age value");
        }
        this.age = age;
    }
}
```
这样一来就杜绝了外部代码所导致的逻辑混乱。

调用方法的格式是`变量.方法名(参数)`

参数的传递是通过参数绑定，基础变量的参数绑定是调用方的复制，双方互不影响。引用变量的参数绑定是调用方的变量和接收方的参数变量都指向同一个变量，任意一方改变这个对象都会对双方产生影响。值得注意的是因为字符串具有不可变性，所以改变双方任意一方无法影响到对方。