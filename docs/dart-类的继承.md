# 类的继承
面向对象的其中一大特性就是继承，继承不仅仅可以减少我们的代码量，也是多态的使用前提。Dart中使用继承使用extends关键字，子类中使用super来访问父类。父类中所有的成员变量和方法都会被继承，但是构造方法除外。
```dart
main(List<String> args) {
  var p = new Person();
  p.age = 18;
  p.run();
  print(p.age);
}

class Animal {
  int age;

  run() {
    print('在奔跑ing');
  }
}

class Person extends Animal {

}
```
子类可以拥有自己的成员变量，并且可以对父类的方法进行重写
```dart
class Person extends Animal {
  String name;

  @override
  run() {
    print('$name在奔跑ing');
  }
}
```
子类中可以调用父类的构造方法，对某些属性进行初始化：
* 子类的构造方法在执行前，将隐含调用父类的无参默认构造方法(没有参数且与类同名的构造方法)
* 如果父类没有无参默认构造方法，则子类的构造方法必须在初始化列表中通过super显式调用父类的某个构造方法。

```dart
class Animal {
  int age;

  Animal(this.age);

  run() {
    print('在奔跑ing');
  }
}
class Person extends Animal {
  String name;

  Person(String name, int age) : name=name, super(age);

  @override
  run() {
    print('$name在奔跑ing');
  }

  @override
  String toString() {
    return 'name=$name, age=$age';
  }
```

