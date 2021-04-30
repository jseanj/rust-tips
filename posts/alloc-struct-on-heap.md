
# struct是分配在栈上还是堆上？
默认是分配在栈上。像Box、大部分容器（Vec、HashMap、Arc、Rc、String等）是分配在堆上。

# struct如何分配在堆上？
比如，有一个struct：
```rust
struct Foo {
    lots_of_bytes: [u8; 1024 * 10],
    bar: bool,
    baz: isize,
}
```
`lots_of_bytes`默认分配在栈上的话很占用空间，所以有两种方式来解决。第一种是将`lots_of_bytes`声明为Box类型：
```rust
struct Foo {
    lots_of_bytes: Box<[u8; 1024 * 10]>,
    bar: bool,
    baz: isize,
}
```
第二种是生成Foo实例时直接用Box封装：
```rust
let foo = Box::new(Foo::new());
```
答主推荐用第一种方式。

参考：
[is-allocating-a-struct-on-the-heap-or-having-a-struct-own-a-heap-pointer-more-id](https://stackoverflow.com/questions/43359599/is-allocating-a-struct-on-the-heap-or-having-a-struct-own-a-heap-pointer-more-id)
