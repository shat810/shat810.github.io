# java作用域
Java中用`public` `protected` `private` 修饰符来设置字段和方法的作用域。

`public`修饰的类和接口，能让其他所有类所访问。
`public`修饰的方法和字段，能让其他所有能访问该类的类所访问。

`protected`修饰的方法，用于继承关系，能让子类或者子类的子类访问。

`private` 修饰的字段和方法，无法被其他类访问。

### 局部变量
定义在方法内部的变量称为局部变量，局部变量只能作用于方法内部。

### final修饰符
用final修饰class可以阻止被继承：

用final修饰method可以阻止被子类覆写：

用final修饰field可以阻止被重新赋值：

用final修饰局部变量可以阻止被重新赋值：
