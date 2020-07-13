## UpperCamelCase

UpperCamelCase 即所有单词首字母大写，其他字母小写，并且没有连接符号，又称驼峰命名法。

Dart 中使用 UpperCamelCase 的情形有

* 类名 Class
* 枚举类型名 enum
* 类型定义 typedef
* 泛型参数
* Extension 名

举例说明

```dart
/// 类名
class MyApp extends StatelessWidget {
}
```

```dart
/// 枚举
enum TextAlign {
  left,
  right,
  center,
  justify,
  start,
  end,
}
```

```dart
/// 类型定义
typedef VoidCallback = void Function();
```

```dart
/// 泛型参数
/// 类的泛型参数 K、V
class NameValuePair<K, V> {
  K name;
  V value;
}

/// 函数的泛型参数 T
Future<T> invokeMethod<T>(String method, [ dynamic arguments ]) async {
}
```

```dart
/// Extension
extension NumberParsing on String {
  int parseInt() {
    return int.parse(this);
  }
  // ···
}
```

