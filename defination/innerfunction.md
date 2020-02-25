# 内置函数 #

工作流提供了内置函数来支持对参数值的一些变换和计算，可以用内置函数来设置参数值，格式如下所示：
```bash
@func("strings#concat", "test1", "test2")
```
@func()表示这是一个内置函数，其中第一个参数"strings#concat"，strings表示函数所属的类，concat是方法名，"test1"，"test2"表示方法参数，这个函数的结果为"test1test2"。

同值运算一样，内置函数还可以和指针进行运算，如下表达式：
```bash
@func("strings#concat", "test1", ${a1.output.p1})
```
它的结果是字符串"test1"拼接在a1的输出的p1字段的值之前，p1字段的类型必须是string，否则函数会报错。

内置函数也可以互相嵌套，例如：
```bash
@func("strings#concat", "test1", @func("strings#concat", "test1", "test2"))
```

## strings ##
```bash
@func("strings#concat", "Hello ", "World!") \\ "Hello World!"
@func("strings#trim", " test ") \\ "test"
@func("strings#trimLeft", "1test", "1") \\ "test"
@func("strings#trimRight", "test1", "1") \\ "test"
@func("strings#replace", "test1", "1", "2") \\ "test2"
```

## convert ##
```bash
@func("convert#int64ToString", 10) \\ "10"
@func("convert#float64ToString", 10.1234, 2) \\ "10.12" 2 digit precision
@func("convert#stringToInt64", "10") \\ 10
@func("convert#stringToFloat64", "10.12") \\ 10.12
@func("convert#isNull", ${workflow.input.p1.value}) \\ 0 or 1
@func("convert#isEqual", ${workflow.input.p1.value}, ${workflow.input.p2.value}) \\ 0 or 1
@func("convert#int64ToFloat64", 1) \\ 1.0
@func("convert#float64ToInt64", 1.0) \\ 1
```

## time ##
```bash
@func("time#now", "America/New_York", "2006-01-02 15:04:05") \\ time now  string format like "xxxx-xx-xx xx:xx:xx"
@func("time#unixNow") \\ unix time
```

## encoding ##
```bash
@func("encoding#toBase64", "test") \\ "dGVzdA=="
@func("encoding#fromBase64", "dGVzdA==") \\ "test"
```

## array ##
```bash
@func("array#append", "STRING", [], "test3") \\ ["test3"]
${workflow.input.p1.value} \\ ["test1", "test2"]
@func("array#append", "STRING", ${workflow.input.p1.value}, "test3") \\ ["test1", "test2", "test3"]
@func("array#len", ${workflow.input.p1.value}) \\ 2
```

## number ##
```bash
@func("number#neg", 1) \\ -1
@func("number#plus", 1.0, 1) \\ 2.0
@func("number#mal", 1.0, 7) \\ 7.0
@func("number#div", 10, 2) \\ 5
```
