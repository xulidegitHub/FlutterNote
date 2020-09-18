# 控制流程语句
你可以通过下面任意一种方式来控制Dart程序流程：
### if and else
和其他语言用法一样，这里有一个注意点：不支持非空即真或者非0即真，必须有明确的bool类型。
```dart
main(List<String> args){
var name = null;
if(name){
print(name)
}
}
```
上面这种做法会报错，因为Dart不支持非空即真操作，必须要有明确的bool值。
```dart
main(List<String> args){
var name = null;
if(name != null){
print(name)
}
}
```
### for循环
进行迭代操作，可以使用标准的for语句。例如：
```dart
for (var i = 0; i < 5; i++) {
  print(i);
}
```
for····in
使用for in遍历List和Set类型
```dart
var names = ['why', 'kobe', 'curry'];
for (var name in names) {
  print(name);
}
```
### while和do-while
while循环在执行前判断执行条件：
```dart
while (!isDone()) {
  doSomething();
}
```
do-while循环在执行后判断执行条件：
```dart
do {
  printLine();
} while (!atEndOfPage());
```
### break和continue
使用break停止程序循环：
```dart
while (true) {
  if (shutDownRequested()) break;
  processIncomingRequests();
}
```
使用continue跳转到下一次迭代：
```dart
for (int i = 0; i < candidates.length; i++) {
  var candidate = candidates[i];
  if (candidate.yearsExperience < 5) {
    continue;
  }
  candidate.interview();
}
```
###switch和case
 Dart 中 switch 语句使用 == 比较整数，字符串，或者编译时常量。 比较的对象必须都是同一个类的实例（并且不可以是子类）， 类必须没有对 == 重写。 枚举类型 可以用于 switch 语句。
在case语句中，每个非空语句结尾必须要跟一个break语句。除了break以外，还有可以使用continue，throw，或者return。case 语句可以拥有局部变量， 这些局部变量只能在这个语句的作用域中可见。
当没有case语句匹配时，执行default代码：
```dart
var command = 'OPEN';
switch (command) {
  case 'CLOSED':
    executeClosed();
    break;
  case 'PENDING':
    executePending();
    break;
  case 'APPROVED':
    executeApproved();
    break;
  case 'DENIED':
    executeDenied();
    break;
  case 'OPEN':
    executeOpen();
    break;
  default:
    executeUnknown();
}
```
### assert
如果assert语句中的布尔条件为false,那么正常的程序执行流程会被中断。
```dart
// 确认变量值不为空。
assert(text != null);

// 确认变量值小于100。
assert(number < 100);

// 确认 URL 是否是 https 类型。
assert(urlString.startsWith('https'));
```
提示：assert语句只在开发环境中有效，在生产环境是无效的。Flutter中的assert只在debug模式下有效。
