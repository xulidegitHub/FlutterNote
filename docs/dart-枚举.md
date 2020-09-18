# 枚举
## 枚举的定义
枚举使用enum关键字来进行定义：
```dart
main(List<String> args) {
  print(Colors.red);
}
enum Colors {
  red,
  green,
  blue
}
```
## 枚举的属性
枚举类型中有两个比较常见的属性：
* index:用于表示每个枚举常量的索引，从0开始。
* value:包含每个枚举值的List。
```dart
main(List<String> args) {
  print(Colors.red);
}
enum Colors {
  red,
  green,
  blue
}
```
可以在 switch 语句 中使用枚举， 如果不处理所有枚举值，会收到警告：
```dart
var aColor = Color.blue;
switch (aColor) {
  case Color.red:
    print('Red as roses!');
    break;
  case Color.green:
    print('Green as grass!');
    break;
  default: // 没有这个，会看到一个警告。
    print(aColor); // 'Color.blue'
}
```
枚举的注意事项：
* 注意一：您不能子类化，混合和实现枚举。
* 主义二：不能显示实例化一个枚举。
