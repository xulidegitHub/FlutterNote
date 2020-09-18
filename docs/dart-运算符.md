# 运算符
## 算术运算符
Dart支持常用的运算的运算符，如下表所示
<table>
    <tr>
        <th>Operator</th>
        <th>Meaning</th>
    </tr>
    <tr>
        <th>+</th>
          <th>Add</th>
    </tr>
    <tr>
      <th>-</th>
      <th>Subtract</th>
    </tr>
    <tr>
      <th>-expr</th>
      <th>Unary minus, also known as negation (reverse the sign of the expression)</th>
    </tr>
    <tr>
     <th>*</th>
     <th>Multiply</th>
    </tr>
    <tr>
    <th>/</th>
    <th>Divide</th>
    </tr>
    <tr>
    <th>~/</th>
    <th>Divide, returning an integer result</th>
    </tr>
    <tr>
    <th>%</th>
    <th>Get the remainder of an integer division (modulo)</th>
    </tr>
</table> 

```dart
assert(2 + 3 == 5);
assert(2 - 3 == -1);
assert(2 * 3 == 6);
assert(5 / 2 == 2.5); // 结果是双浮点型
assert(5 ~/ 2 == 2); // 结果是整型
assert(5 % 2 == 1); // 余数
assert('5/2 = ${5 ~/ 2} r ${5 % 2}' == '5/2 = 2 r 1');
```
Dart还支持前缀和后缀，自增自减运算符。
<table>
    <tr>
        <th>Operator</th>
        <th>Meaning</th>
    </tr>
    <tr>
        <th>++var</th>
          <th>var = var + 1 (expression value is var + 1)</th>
    </tr>
    <tr>
      <th>var++</th>
      <th>var = var + 1 (expression value is var)</th>
    </tr>
    <tr>
      <th>--var</th>
      <th>var = var – 1 (expression value is var – 1)</th>
    </tr>
    <tr>
     <th>var--</th>
     <th>var = var – 1 (expression value is var)</th>
    </tr>
</table> 

```dart
var a, b;

a = 0;
b = ++a; // a自加后赋值给b。
assert(a == b); // 1 == 1

a = 0;
b = a++; // a先赋值给b后，a自加。
assert(a != b); // 1 != 0

a = 0;
b = --a; // a自减后赋值给b。
assert(a == b); // -1 == -1

a = 0;
b = a--; // a先赋值给b后，a自减。
assert(a != b); // -1 != 0
```
## 关系运算符
下表列出了关系运算符及含义：
<table>
    <tr>
        <th>Operator</th>
        <th>Meaning</th>
    </tr>
    <tr>
        <th>==</th>
          <th>Equal; see discussion below</th>
    </tr>
    <tr>
      <th>!=</th>
      <th>Not equal</th>
    </tr>
    <tr>
      <th>></th>
      <th>Greater than</th>
    </tr>
    <tr>
     <th><</th>
     <th>Less than</th>
    </tr>
    <tr>
       <th><=</th>
       <th>Less than or equal to</th>
      </tr>
</table> 
要测试两个对象x和y是否表示相同的事物，使用==运算符。在极少数情况下，要确定两个对象是否完全相同，需要使用identical()函数。下面给出==的运算符的工作原理：

* 如果 x 或 y 可以 null，都为 null 时返回 true ，其中一个为 null 时返回 false。
* 结果为函数 x.==(y) 的返回值。 (如上所见, == 运算符执行的是第一个运算符的函数。 我们甚至可以重写很多运算符，包括 ==， 运算符的重写，参考 重写运算符。）
这里列出了每种关系运算符的示例：

```dart
assert(2 == 2);
assert(2 != 3);
assert(3 > 2);
assert(2 < 3);
assert(3 >= 3);
assert(2 <= 3);
```
## 类型判定运算符
as,is,is！运算符用于在运行时处理类型检查。
<table>
    <tr>
        <th>Operator</th>
        <th>Meaning</th>
    </tr>
    <tr>
        <th>as</th>
          <th>Typecast (也被用于指定库前缀)</th>
    </tr>
    <tr>
      <th>is</th>
      <th>True if the object has the specified type</th>
    </tr>
    <tr>
      <th>is!</th>
      <th>False if the object has the specified type</th>
</table>

## 赋值运算符
使用=为变量赋值。使用 ??= 运算符时，只有当被赋值的变量为 null 时才会赋值给它。

```dart
// 将值赋值给变量a
a = value;
// 如果b为空时，将变量赋值给b，否则，b的值保持不变。
b ??= value;
```
复合赋值运算符（如 += ）将算术运算符和赋值运算符组合在了一起。
<table>
    <tr>
        <th>=</th>
        <th>–=</th>
        <th>/=</th>
        <th>%=</th>
        <th>>>=</th>
        <th>^=</th>
    </tr>
    <tr>
        <th>+=</th>
        <th>*=</th>
        <th>~/=</th>
        <th><<=</th>
        <th>&=</th>
        <th>|=</th>
    </tr>
</table>
以下说明符合赋值运算符的作用:
<table>
<tr>
<th> </th>
<th>Compound assignment</th>
<th>Equivalent expression</th>
</tr>
<tr>
<th>For an operator op:</th>
<th>a op= b</th>
<th>a = a op b</th>
</tr>
<tr>
<th>Example:</th>
<th>a += b</th>
<th>a = a + b</th>
</tr>
</table>

## 逻辑运算符
逻辑操作符可以反转或组合布尔表达式。
<table>
    <tr>
        <th>Operator</th>
        <th>Meaning</th>
    </tr>
    <tr>
        <th>!expr</th>
        <th>inverts the following expression (changes false to true, and vice versa)</th>
    </tr>
    <tr>
           <th>||</th>
           <th>logical OR</th>
       </tr>
       <tr>
                <th>&&</th>
                <th>logical AND</th>
            </tr>
</table>
以下说明符合赋值运算符的作用:

```dart
if (!done && (col == 0 || col == 3)) {
  // ...Do something...
}
```
## 按位和移位运算符
在Dart中，可以单独操作数字的某一位。通常情况下整数类型使用按位和移位运算符来操作。
<table>
    <tr>
        <th>Operator</th>
        <th>Meaning</th>
    </tr>
    <tr>
        <th>&</th>
        <th>AND</th>
    </tr>
    <tr>
           <th>|</th>
           <th>OR</th>
       </tr>
       <tr>
           <th>^</th>
           <th>XOR</th>
       </tr>
       <tr>
                <th>~expr</th>
                <th>Unary bitwise complement (0s become 1s; 1s become 0s)</th>
            </tr>
            <tr>
                          <th><<</th>
                          <th>Shift left</th>
                      </tr>
                      <tr>
                                               <th>>></th>
                                               <th>Shift right</th>
                                           </tr>
</table>
下面是关于按位和移位运算符的实例：

```dart
final value = 0x22;
final bitmask = 0x0f;

assert((value & bitmask) == 0x02); // AND
assert((value & ~bitmask) == 0x20); // AND NOT
assert((value | bitmask) == 0x2f); // OR
assert((value ^ bitmask) == 0x2d); // XOR
assert((value << 4) == 0x220); // Shift left
assert((value >> 4) == 0x02); // Shift right
```
## 条件表达式
Dart有两个运算符，有时可以替换 if-else 表达式， 让表达式更简洁：
* condition ? expr1 : expr2
如果条件为 true, 执行 expr1 (并返回它的值)： 否则, 执行并返回 expr2 的值。
* expr1 ?? expr2
如果 expr1 是 non-null， 返回 expr1 的值； 否则, 执行并返回 expr2 的值。
如果赋值是根据布尔值， 考虑使用 ?:。
```dart
var visibility = isPublic ? 'public' : 'private';
```
如果赋值是基于判定是否为 null， 考虑使用 ??。
```dart
String playerName(String name) => name ?? 'Guest';
```
下面给出了其他两种实现方式， 但并不简洁：
```dart
// Slightly longer version uses ?: operator.
String playerName(String name) => name != null ? name : 'Guest';
// Very long version uses if-else statement.
String playerName(String name) {
  if (name != null) {
    return name;
  } else {
    return 'Guest';
  }
}
```
## 级联运算符 (..)
级联运算符 (..) 可以实现对同一个对像进行一系列的操作。 除了调用函数， 还可以访问同一对象上的字段属性。 这通常可以节省创建临时变量的步骤， 同时编写出更流畅的代码。某些时候，我们希望对一个对象进行连续的操作，这个时候可以使用级联语法。
```dart
class Person {
  String name;

  void run() {
    print("${name} is running");
  }

  void eat() {
    print("${name} is eating");
  }

  void swim() {
    print("${name} is swimming");
  }
}
main(List<String> args) {
  final p1 = Person();
  p1.name = 'why';
  p1.run();
  p1.eat();
  p1.swim();

  final p2 = Person()
              ..name = "why"
              ..run()
              ..eat()
              ..swim();
}
```



