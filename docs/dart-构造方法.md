# 构造方法 
## 普通构造方法
当通过类创建一个对象的时候，会调用这个类的构造方法。
* 当类中没有明确指定构造方法的时候，将默认会拥有一个无参的构造方法。
也可以根据自己的需求，自定义构造方法。
    * 注意一：当有了自己的构造方法的时候，默认构造方法将会失效，不能使用。

```dart
class Person {
  String name;
  int age;

  Person(String name, int age) {
    this.name = name;
    this.age = age;
  }

  @override
  String toString() {
    return 'name=$name age=$age';
  }
}
```
另外，在实现构造方法时，通常做的事情就是通过**参数给属性**赋值
为了简化这一过程, Dart提供了一种更加简洁的语法糖形式.
上面的构造方法可以优化成下面的写法：
```dart
 Person(String name, int age) {
    this.name = name;
    this.age = age;
  }
  // 等同于
  Person(this.name, this.age);
  ```
## 命名构造函数
因为dart中不支持函数重载，但是开发中，我们确实希望实现更多的构造方法，怎么办呢？
* 使用命名构造方法

```dart
class Person {
  String name;
  int age;

  Person() {
    name = '';
    age = 0;
  }
	// 命名构造方法
  Person.withArgments(String name, int age) {
    this.name = name;
    this.age = age;
  }

  @override
  String toString() {
    return 'name=$name age=$age';
  }
}

// 创建对象
var p1 = new Person();
print(p1);
var p2 = new Person.withArgments('why', 18);
print(p2);
```
## 初始化列表
### *什么是初始化列表？

我们可以在构造函数体执行之前初始化实例变量。各参数的初始化用逗号隔开。
初始化列表是在构造函数方法体执行之前，初始化参数的值。
```dart
import 'dart:math';

class Point {
  final num x;
  final num y;
  final num distanceFromOrigin;

  Point(x, y)
      : x = x,
        y = y,
        distanceFromOrigin = sqrt(x * x + y * y);
}

main() {
  var p = new Point(2, 3);
  print(p.distanceFromOrigin);
}

```
