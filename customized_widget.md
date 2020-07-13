## 自定义 Widget

### 通过组合的方式定义Widget

Flutter 自定义 Widget 应优先考虑组合的方式，将基础的 Widget 组装成复杂的 Widget。

如非必须自己管理状态，则优先继承 StatelessWidget，由父 Widget 管理状态。

> 以按钮为例，一般有普通状态和按下状态，这两种状态的切换与父 Widget 无关，完全由自己管理，所以按钮一般继承自 StatefulWidget。
>
> 而 Text 之类的 Widget，其内容如何显示完全由外部决定，这种只需要继承 StatelessWidget 即可。
>
> 再比如 TabBar 这一类的 Widget，切换 Tab 之后，不仅自身状态需要更新，外部的页面也需要切换，这种 Widget 的状态可以自己管理，也可以交给父 Widget 管理，所以继承 StatefulWidget 或 StatelessWidget 都可以。



### 构造函数和成员变量

Widget 类是被标记为 `@immutable` 的，所以不管是 `StatelessWidget` 还是 `StatefulWidget` ，成员变量都应该声明为 `final` 。

对于构造函数并没有要求必须为 `const` ，但应该优先考虑定义为 `const` 类型。