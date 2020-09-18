# 定义变量
### 明确声明
明确声明变量的方式，格式如下：
```dart
变量类型 变量名称 = 赋值;
```
示例代码：
```dart
String name = 'coderwhy';
int age = 18;
double height = 1.88;
print('${name}, ${age}, ${height}'); // 拼接方式后续会讲解
```
注意事项：定义的变量可以修改值，但是不能赋值给其他类型。
```dart
String content = 'Hello Dart';
content = 'Hello World'; // 正确的
content = 111; // 错误的, 将一个int值赋值给一个String变量
```
### 类型推导
类型推导声明变量的方式，格式如下：
```dart
var/dynamic/const/final 变量名称 = 赋值;
```
