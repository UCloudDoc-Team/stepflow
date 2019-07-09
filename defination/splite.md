{{indexmenu_n>22}}

# 并行逻辑

并行逻辑 SplitDecision 的功能用于让用户可以并行处理一些微服务，常和 合并逻辑 MergDecision一起使用。

## SplitDecision 示意图

![](http://stepflow-docs.cn-bj.ufileos.com/splite001.png)

## SplitDecision 定义

    {
      "branches": [
        "StepA",
        "StepB"，
        "StepC"
      ]
    }

备注：StepA，StepB，StepC表示并行的步骤名

## 创建 SplitDecision

![](http://stepflow-docs.cn-bj.ufileos.com/function002.png)

分支选择需要并行处理的步骤名 ![](http://stepflow-docs.cn-bj.ufileos.com/split003.png)
