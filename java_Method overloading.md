# java方法重载
方法重载就是在一个类中定义多个同名方法，但是参数的个数和顺序不同
 ```java
 class Hello {
    public void hello() {
        System.out.println("Hello, world!");
    }

    public void hello(String name) {
        System.out.println("Hello, " + name + "!");
    }

    public void hello(String name, int age) {
        if (age < 18) {
            System.out.println("Hi, " + name + "!");
        } else {
            System.out.println("Hello, " + name + "!");
        }
    }
}
 ```
 重载方法的返回类型应该相同。