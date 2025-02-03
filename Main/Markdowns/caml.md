# CAML(Cam's Awesome Markup Language)
cam自己搞的一套描述型脚本语言，目前仅用于IR。

功能等效于json，语法很像Python。

[这个](https://teamopenindustry.cc/caml/)工具可以将json文件转换为caml文件。

caml文件在IR开发中等效于json文件，即对于我下面讲的abc.json，你可以用abc.caml进行替换。但是方便起见，大部分情况下我还是会使用json来讲。

> 24/02/13填坑：我认为还是有必要说一下

caml类似Python的点在于：
1.它以缩进来区分代码块，而不是大括号。
```caml
attribute:
    value = "Hello!"
```

2.如果有不属于字符串中的`#`，那么它及同一行之后的文本会被忽略（即成为注释）。
```caml
attribute:
    value = "Hello!" #这是注释！
```

此外，`=`连接的键不可重复，而`:`的键则可以。翻译过来就是，caml中的`=`对应json中的`:`，而caml中的`:`用来表示数组。

caml中没有表示数组（json中`[`和`]`）的方法，我们需要重复一个语句多次，比如：
```json
{
    "comment": [
        "Hello",
        "world!"
    ]
}
```
```caml
    comment: "Hello"
    comment: "world!"
```

caml中的键不用加双引号，这是与json区别的另一点；而caml中的值仅当其是字符串需要加双引号，枚举值不需要。