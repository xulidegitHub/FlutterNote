# 隐式接口
Dart中的接口比较特殊，没有一个专门的关键字来声明接口。默认情况下，定义的每个类都相当于默认也声明了一个接口，可以由其他的类来实现，因为Dart不支持多继承。在开发中，我们通常将用于给别人实现的类声明为抽象类：一个类可以通过 implements 关键字来实现一个或者多个接口， 并实现每个接口要求的 API。 例如：
```dart
abstract class Runner {
  run();
}

abstract class Flyer {
  fly();
}

class SuperMan implements Runner, Flyer {
  @override
  run() {
    print('超人在奔跑');
  }

  @override
  fly() {
    print('超人在飞');
  }
}

```