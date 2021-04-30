
# String 转 &str 的方式
我们先来看一段代码：
```rust
fn main() {
    let stringthing = String::from("c");
    match stringthing {
        String::from("a") => println!("0"),
        String::from("b") => println!("1"),
        String::from("c") => println!("2"),
    }
}
```
这段代码会报错，表示模式匹配时不能使用方法。那么我们将String转成&str来进行匹配，有四种方式。
第一种：
```rust
match &stringthing[..] {
    "a" => println!("0"),
    "b" => println!("1"),
    "c" => println!("2"),
    _ => println!("something else!"),
}
```
第二种：
```rust
match stringthing.as_str() {
    "a" => println!("0"),
    "b" => println!("1"),
    "c" => println!("2"),
    _ => println!("something else!"),
}
```
第三种：
```rust
match stringthing.as_ref() {
    "a" => println!("0"),
    "b" => println!("1"),
    "c" => println!("2"),
    _ => println!("something else!"),
}
```
第四种：
```rust
match &stringthing as &str {
    "a" => println!("0"),
    "b" => println!("1"),
    "c" => println!("2"),
    _ => println!("something else!"),
}
```

参考：[how-to-match-a-string-against-string-literals](https://stackoverflow.com/questions/25383488/how-to-match-a-string-against-string-literals)