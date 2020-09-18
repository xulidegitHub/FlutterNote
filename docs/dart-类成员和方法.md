# 类成员和方法
前面我们在类中定义的成员和方法都属于对象级别的，在开发中，我们有时候也需要定义类级别的成员和方法。在Dart中，我们使用static关键字来定义：
```dart
main(List<String> args) {
  var stu = Student();
  stu.name = 'why';
  stu.sno = 110;
  stu.study();

  Student.time = '早上8点';
  // stu.time = '早上9点'; 错误做法, 实例对象不能访问类成员  
 ‍‍‍Student.attendClass();  // stu.attendClass(); 错误做法, 实现对象不能‍访问类方法
}
class Student {
  String name;
  int sno;

  static String time;

  study() {
    print('$name在学习');
  }

  static attendClass() {
    print('去上课');
  }
}
```
