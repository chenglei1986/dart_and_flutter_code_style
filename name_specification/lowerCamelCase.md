## lowerCamelCase

lowerCamelCase 即第一个单词首字母小写，之后的单词首字母大写的驼峰命名法。

Dart 中使用 lowerCamelCase 的情形有

* 类成员（字段、方法）
* 变量（全局变量、局部变量）
* 常量/枚举值
* 函数名和函数参数名

举例说明

```dart
/// 类成员
class Color {
  
  /// 方法
  Color withAlpha(int a) {
    return Color.fromARGB(a, red, green, blue);
  }
  
  /// 字段
  final int value;
}

/// 变量
int value;

/// 运行时常量
final int value;

/// 编译时常量
const int value;

enum Week {
  /// 枚举值
  mon,
  tue,
  wed,
  thu,
  fri,
  sat,
  sun,
}

/// 函数名
static bool isNotEmpty(
  String text // 函数参数名
) {
  return text != null && text.length > 0;
}
```

