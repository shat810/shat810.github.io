# java面向对象编程
面向对象编程，首先你得有个对象，对象是什么呢？对象在现实生活中就是一个个人或者事物。然后面向对象编程就是把现实中对象抽象到计算机的世界里面。

人这个对象在java就抽象为一个类Person类`class Person{}`。具体的某一个人就是一个实例。

小明实例化对象就是`Person ming = new Person();`实例化一个对象然后用变量ming指向它。

就像每一个具体的人有名字有年龄有性别一样，在每一个实例中又有各种字段，例如：
```java
class Person{
    public String name;
    public String sex;
    public int age;
}
```
具体每一个实例的属性调用的方法是`变量.字段`,例如给小明的名字赋值`ming.name = "小明";`
