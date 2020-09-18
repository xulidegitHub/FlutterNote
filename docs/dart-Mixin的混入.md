# Mixin混入
在通过implements实现某个类的时候，类中所有的方法都必须被重新实现，无论这个类原来是否已经实现过该方法。但是某些情况下，一个类可能希望直接复用之前类的原有实现方案，怎么做呢？
* 使用继承吗？但是Dart支持单继承，那么意味着你只能复用一个类的实现，Dart提供了另外一种方案：Mixin混入的方式
* 除了可通过class定义类之外，也可以通过mixin关键字来定义一个类。
* 只是通过mixin定义的类用于被其他类混入使用，通过with关键字来进行混入。

```dart
main(List<String> args) {
  var superMan = SuperMain();
  superMan.run();
  superMan.fly();
}
mixin Runner {
  run() {
    print('在奔跑');
  }
}
mixin Flyer {
  fly() {
    print('在飞翔');
  }
}
// implements的方式要求必须对其中的方法进行重新实现
// class SuperMan implements Runner, Flyer {}
class SuperMain with Runner, Flyer {}
```
