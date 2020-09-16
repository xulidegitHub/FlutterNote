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
初始化列表是在构造函数方法体执行之前，初始化参数的值。与其他函数不同，构造函数除了有名字，参数列表和函数体之外，还可以有初始化列表，初始化列表以冒号开头，后跟一系列以逗号分隔的初始化字段。

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
### *执行阶段？
从概念上来讲，构造函数的执行可以分成两个阶段，初始化阶段和计算阶段，初始化阶段先于计算阶段。
### *执行阶段？
初始化阶段？
所有类类型成员都会在初始化阶段初始化，即使该成员没有出现在构造函数的初始化列表中
### *计算阶段？
一般用于执行构造函数体内的赋值操作。
### *使用原因？
初始化类的成员有两种方式，一是使用初始化列表，二是在构造函数体内进行赋值操作。
主要是性能问题，对于内置类型，如int,float等，使用初始化类表和在构造函数体内初始化差别不是很大，但是对于类类型来说，最好使用初始化列表。
## 重定向构造方法
在某些情况下，我们希望在一个构造方法中去调用另外一个构造方法，这个时候可以使用重定向构造方法：在一个构造函数中，去调用另外一个构造函数（注意：在冒号后面使用this调用）重定向构造函数的函数体为空，构造函数的调用在冒号之后。
```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);
  //指向主构造函数
  Person.fromName(String name) : this(name, 0);
}
```
## 常量构造函数
在某些情况下，传入相同的值，我们希望返回同一个对象，这个时候，可以使用常量构造方法。默认情况下，创建对象时，即使传入相同的参数，创建出来的也不是同一个对象，看下面代码：
```dart
main(List<String> args) {
  var p1 = Person('why');
  var p2 = Person('why');
  print(identical(p1, p2)); // false
}

class Person {
  String name;

  Person(this.name);
}
```
但是，如果将构造方法前面添加const进行修饰，那么可以保证同一个参数，创建出来的对象是相同的，这样的构造方法我们称为常量构造方法。
常量构造方法注意点：
* 注意一：拥有常量构造方法的类中，所有的成员变量必须是final修饰的。
* 注意二：为了可以通过常量构造方法，创建出相同的对象，不再使用new关键字，而是使用const关键字。
** 如果将结果赋值给const修饰的标示符，const可以省略。

## 工厂构造方法
当执行构造函数并不总是创建这个类的一个新实例的时候，则使用factory关键字。例如：一个工厂构造函数可能会返回一个cache中的实例，或者可能返回一个子类的实例。
```dart
Dart提供了factory关键字，用于通过工厂去获取对象
main(List<String> args) {
  var p1 = Person('why');
  var p2 = Person('why');
  print(identical(p1, p2)); // true
}

class Person {
  String name;

  static final Map<String, Person> _cache = <String, Person>{};

  factory Person(String name) {
    if (_cache.containsKey(name)) {
      return _cache[name];
    } else {
      final p = Person._internal(name);
      _cache[name] = p;
      return p;
    }
  }

  Person._internal(this.name);
}
```
* 工厂构造函数无法访问this
