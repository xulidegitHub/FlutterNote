# 抽象类
我们知道，继承是多态使用的前提，所以在定义很多通用** 调用接口 **的时候，我们通常会让调用者传入父类，通过多态来实现更加灵活的调用方式。但是，父类本身可能并不需要对某些方法进行具体实现，所以父类中定义的方法，我们可以定义为抽象方法。
## 什么是抽象方法？
* 抽象方法，必须存在于抽象类中。
* 抽象类是使用abstract声明的类。
* 抽象方法只存在于抽象类中。
下面的代码中，Shape类就是一个抽象类，其中包含一个抽象方法。

```dart
abstract class Shape {
  getArea();
}

class Circle extends Shape {
  double r;

  Circle(this.r);

  @override
  getArea() {
    return r * r * 3.14;
  }
}

class Reactangle extends Shape {
  double w;
  double h;

  Reactangle(this.w, this.h);

  @override
  getArea() {
    return w * h;
  }
}
```

注意事项：
* 注意一：**抽象类不能实例化。
* 注意二：**抽象类中的抽象方法必须被子类实现，抽象类中的已经被实现方法，可以不被子类重写。

