{{indexmenu_n>2}}

# 内置函数

StepFlow 为方便用户，将一些常用功能包装在了参数定义中。后续会持续将用户需求转化成内置函数。

\======= base64encode ======= 功能：

将用户的值进行BASE64转码

使用方式：

在用户的初入参值的填写中，按以下方式填写参数。

    @func(base64encode, `foo`)

foo表示实参

\======= base64decode =======

功能：

将用户的值进行BASE64解码

使用方式：

在用户的出入参值的填写中，按以下方式填写参数。

    @func(base64decode, `foo`)

foo表示实参

\======= concat =======

功能：

对输入的参数进行拼接, 并返回拼接后的字符串

使用方式：

在用户的出入参值的填写中，按以下方式填写参数。

    @func(concat, [input1], [input2], ...)

input: string|number, 作为输入

output: string, 将所有 \[input\] 拼接后, 返回拼接完成的字符串

\======= replace =======

功能：

字符串替换

使用方式：

在用户的出入参值的填写中，按以下方式填写参数。

    @func(replace, [input], [old], [new])

input: string, 作为输入

old: string, 被替换值

new: string, 替换值

例如： 想将字符串“month=08”中的“08”作为每次工作流调用时候的一个动态值。可以这么写

@func(replace,`month=$month`,`$month`,`${workflow.input.month}`)  将$month作为了一个替换符。

