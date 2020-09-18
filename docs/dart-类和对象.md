# 类和对象
Dart是一个面向对象的语言，面向对象中非常重要的概念就是类，类产生了对象。
### 类的定义
在Dart中，定义类用class关键字。类通常有两部分组成：成员和方法。
```dart
class 类名 {
  类型 成员名;
  返回值类型 方法名(参数列表) {
    方法体
  }
}
```
编写一个简单的Person类：
* 这里有一个注意点：我们在方法中使用属性，并没有添加this;
* Dart的开发风格中，在方法中通常使用属性时，会省略this.但是有命名冲突的时候，this不能省略。
```dart
class Person {
  String name;

  eat() {
    print('$name在吃东西');
  }
}
```
我们来使用这个类，创建对应的对象：
* 注意，从Dart2开始，new关键字可以省略
```dart
main(List<String> args) {
  // 1.创建类的对象
  var p = new Person(); // 直接使用Person()也可以创建

  // 2.给对象的属性赋值
  p.name = 'why';

  // 3.调用对象的方法
  p.eat();
}
```
