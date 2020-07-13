## 代码风格与最佳实践

### 缩进

Dart 和 Flutter 的代码缩进均为 2 个空格。



### 避免 var 的使用

应避免使用 var 定义变量。

虽然 Dart 支持类型推导，但代价是更长的编译和执行时长，同时也会降低代码的可读性，在 Dart 和 Flutter 源码以及流行三方库中极少使用。



### 函数的定义

Dart 不支持函数重载，要实现类似功能时，应优先考虑使用 **命名可选参数**。

使用命名可选参数的函数更容易进行扩展，符合开闭原则，即对修改关闭，对扩展开放。



### 命名参数后的逗号

函数调用时，最后一个命名可选参数后应加上一个逗号，从而保证自动格式化正常运行。



### 避免 part 和 part of 的使用

`part` 和 `part of` 目前更多的使用在自动生成的代码中，在 `package` 中也有使用，但总体来说不推荐使用，因为会导致代码不易理解和维护，开发组在未来可能会将它们移除或引入新特性替代。



### 使用 `?.` 判空

使用对象成员访问运算符之前，一般要进行判空，一般的写法是

```dart
if (foo != null) {
  foo.bar();
}
```

Dart 中可以这样写

```dart
foo?.bar();
```

两种写法等价。



### `??` 符号的使用

举例说明

```dart
if (optionalThing.isEnabled) {
  print("Have enabled thing.");
}
```

如果 `optionalThing` 为 `null`，则会引起异常，虽然 `?.` 可以判空，但如果改写如下则会引起其他问题

```dart
if (optionalThing?.isEnabled) {
  print("Have enabled thing.");
}
```

`optionalThing?.isEnabled` 在 `optionalThing` 不为 `null` 时返回一个布尔值，但在 `optionalThing` 为 `null` 时返回 `null`，这在 dart 中会引起异常，某些语言中 `null` 可以代表 `false`，在 dart 中不可以。

如果用 `??` 运算符则可以这样写

```dart
if (optionalThing?.isEnabled ?? false) {
  print("Have enabled thing.");
}
```



### 集合

##### 初始化

Dart 中应尽量避免使用构造函数创建集合，推荐的写法如下

```dart
List points = [];
List<String> names = [];
var items = <Item>[];

Map addresses = {};
Map<String, dynamic> headers = {};
var body = <String, dynamic>{};
```

但如果要创建一个定长的数组，则应使用构造函数

```dart
List<String> names = List(10);
names[0] = 'John'; // OK
names.add('Bill'); // 定长数组不能添加元素，会抛异常 Unsupported operation: Cannot add to a fixed-length list
```

##### 判空

集合的判空应使用内建 getter 函数 isEmpty 和 isNotEmpty，不能使用 length，因为效率低下。

##### 遍历

数组遍历的方法及效率对比如下

```dart
/// for 循环 效率最高
for (var i = 0; i < names.length; i++) {
  // do something
}

/// forEach 效率第二
names.forEach((name) {
  // do something
});

/// for-in 效率最低
for (var name in names) {
  // do something
}
```

经过实测（i5-7360U/16G），执行效率对比如下

![](images/loop_effeciency.png)



