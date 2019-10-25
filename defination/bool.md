

# 是非逻辑

是非逻辑 BoolDecision在工作流里起到了是非判断的作用。

## BoolDecision 示意图

![](http://stepflow-docs.cn-bj.ufileos.com/bool001.png)

## BoolDecision 定义

    {
      "express": {
        "left": {
          "Name": "UserID",                      //判断左值
          "Type": "INT64",                       
          "value": "${workflow.Input.UserID}"      
        },
        "operation": "EQ",                       //运算符：EQ=“相等”，LT=“小于”，GT=“大于”
        "right": 0                               //判断右值
      },
      "false": "step001",                        //不满足条件时步骤名
      "true": "step002"                          //满足条件时步骤名
    }

## 创建BoolDecision

![](http://stepflow-docs.cn-bj.ufileos.com/decision001.png)
