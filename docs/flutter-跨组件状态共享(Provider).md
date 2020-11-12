# 跨组件状态共享（Provider）
在Flutter开发中，状态管理是一个永恒的话题。一般的原则是：如果状态是组件私有的，则应该由组件自己管理：如果状态要跨组件共享，则该状态应该由各个组件共同的父元素来管理。对于组件私有的状态管理很好理解，但对于跨组件共享的状态，管理的方式就比较多了，如使用全局事件总线EventBus.它是一个观察者模式的实现，通过它就可以实现跨组件状态同步：状态持有方（发布者）负责更新，发布状态，状态使用方监听状态改变事件来执行一些操作。
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
