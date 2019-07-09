{{indexmenu_n>27}}

# 计数器

计数器 PlusDecision常用于循环过程中，配合BoolDecision，达到do while的效果。

## PlusDecision 输入

![](http://stepflow-docs.cn-bj.ufileos.com/plus001.png)

init：初始值，默认为0

step：每次出发增加值

备注：

1 init，step 都为INT64

2 支持输入变量，如${step001.output.param}，变量需要是INT64类型。

## PlusDecision 输出

num：当前计数值

调用num方式：${stepname.output.num}

stepname为该步骤名称。
