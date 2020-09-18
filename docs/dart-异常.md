# 异常
Dart 代码可以抛出和捕获异常。 异常表示一些未知的错误情况。 如果异常没有被捕获， 则异常会抛出， 导致抛出异常的代码终止执行。
### throw
```dart
throw FormatException('Expected at least 1 section');
throw 'Out of llamas!';
```
### try catch
通过指定多个catch语句，可以处理可能抛出多种类型异常代码。与抛出异常类型匹配的第一个catch语句处理异常。如果catch语句未指定类型，则该语句可以处理任何类型的抛出对象：
```dart
try {
  breedMoreLlamas();
} on OutOfLlamasException {
  // 一个特殊的异常
  buyMoreLlamas();
} on Exception catch (e) {
  // 其他任何异常
  print('Unknown exception: $e');
} catch (e) {
  // 没有指定的类型，处理所有异常
  print('Something really unknown: $e');
}
```
### finally
不管是否抛出异常，finally中的代码都会被执行。如果catch没有匹配到异常，异常会在finally执行完成后，再次被抛出
```dart
try {
  breedMoreLlamas();
} catch (e) {
  print('Error: $e'); // Handle the exception first.
} finally {
  cleanLlamaStalls(); // Then clean up.
}
```
