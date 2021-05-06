`String` 是堆类型，和 `Vec` 类似，当你需要持有（比如不同线程传递字符串，或者在运行时创建字符串）或者修改字符串数据时使用它。
`String` 类型的变量是胖指针，包括指向堆内存的指针，字符串长度、字符串容量

`str` 的含义直接用英文更准确些：
>>> str is an immutable sequence of UTF-8 bytes of dynamic length somewhere in memory

这里 `immutable` 表示 `str` 是固定长度的，`dynamic` 表示 `str` 的长度在编译时是无法确定的，所以需要配合指针来用（即`&str`）。
`&str` 类型的变量是胖指针，包括指向堆内存的指针，字符串长度

切片可以看作是一些数据的视图，这些数据可以存储在任何地方：
- 静态空间，比如字符串常量"foo"的类型是&'static str。数据是硬编码进可执行程序，在程序运行时加载到内存。
- 堆空间，比如 `String` 类型。
- 栈空间，比如下面分配了一个栈空间的字节数组，然后获取 &str。

```rust
use std::str;

let x: &[u8] = &[b'a', b'b', b'c'];
let stack_str: &str = str::from_utf8(x).unwrap();
```

相似：
String 和 Vec<T>
&str 和 &[T]
T 和 &T

[what-are-the-differences-between-rusts-string-and-str/24159933#24159933](https://stackoverflow.com/questions/24158114/what-are-the-differences-between-rusts-string-and-str/24159933#24159933)