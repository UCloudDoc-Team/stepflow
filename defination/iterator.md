{{indexmenu_n>28}}

# 迭代器

迭代器 IterateDecision 用于实现foreach 功能。

## IterateDecision 输入

![](http://stepflow-docs.cn-bj.ufileos.com/iterate001.png)

type: 数组元素类型，除数组以外类型

Value: \[\] 值数组

## IterateDecision 输出

默认输出 ${stepname.output.i} ，0为未完成，-1为完成

默认输出 ${stepname.output.v}，当前迭代的值。

stepname为该步骤名
