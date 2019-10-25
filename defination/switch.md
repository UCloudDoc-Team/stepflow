

# 分支逻辑

分支逻辑 SwitchDecision在工作流里起到了分支条件的作用。

## SwitchDecision 示意图

![](http://stepflow-docs.cn-bj.ufileos.com/switch001.png)

## SwitchDecision 输入模版

    {
      "express": {
        "name": "switch",                       
        "type": "INT64",
        "value": "${workflow.input.id}"        //定义switch分支value来源
      },
      "default": "defaultactivity",            //当不满足任何一个switch分支条件所走的默认下一步骤
      "cases": [
        {
          "value": 0,                          //分支判断值，可自行增加分支数量 
          "next": "case1"                      //下一步骤名
        },
        {
          "value": 1,
          "next": "case2"
        }
      ]
    }

## 创建SwitchDecision

![](http://stepflow-docs.cn-bj.ufileos.com/decision001.png)
