# java 包
Java使用包来区分相同名字的类。

例如小明和小红都创建了一个Peoson类。
这时候就需要用包来区分。

小明的Person类存放在ming这个包下面他的完整类名为`ming.Person`

小红的Person类存放在hong这个包下面他的完整类名为在`hong.Person`。

如果我想使用小明的Person类我就需要引入他的ming包。Java中使用`import`引入。`import ming` 使用小红的就`import hong`.

### 包作用域
在同一个包下，没有用修饰符来修饰的方法和字段都是包作用域的内容，可以被所有在同一个包中的类使用。
```java
package hello;

public class Person {
    // 包作用域:
    void hello() {
        System.out.println("Hello!");
    }
}

Main类也定义在hello包下面：

package hello;

public class Main {
    public static void main(String[] args) {
        Person p = new Person();
        p.hello(); // 可以调用，因为Main和Person在同一个包
    }
}
```