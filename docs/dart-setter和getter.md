# setter和getter
setter和getter是用于对象属性读和写的特殊方法。回想之前的例子，每个实例变量都有一个隐式的getter，通常情况下还会有一个setter。使用get和set关键字实现getter和setter，能够为实例创建额外的属性。默认情况下，Dart类定义的属性是可以直接被外界访问的。但是某些情况下，我们希望监控这个类的属性被访问的过程，这个时候就可以使用setter和getter了。
```dart
main(List<String> args) {
  final d = Dog("黄色");
  d.setColor = "黑色";
  print(d.getColor);
}

class Dog {
  String color;

  String get getColor {
    return color;
  }
  set setColor(String color) {
    this.color = color;
  }

  Dog(this.color);
}
```