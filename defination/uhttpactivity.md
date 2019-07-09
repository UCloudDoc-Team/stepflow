{{indexmenu_n>20}}

# UHttp步骤

UHttp步骤 UHttpActivity作为工作流服务里执行UCloud
Api的定制步骤。使用此步骤需要先进行UAPI授权。StepFlow根据授权会获取用户的公司钥进行定制步骤的执行。

## UHttpActivity 示意图

![](http://stepflow-docs.cn-bj.ufileos.com/uhttp001.png)

## UHttpActivity 输入模版

    {
      "url": "https://api.ucloud.cn",
      "body": {
        "Action": "DescribeEIP",                   //实际所需要调用的UCloud API
        "Region": "${workflow.input.Region}"       //UCloud API 入参
      },
      "header": {
        "ContentType": "application/json"
      },
      "method": "POST",
      "isAsync": false,
      "timeout": 0,
      "retrytimes": 0
    }

## 创建HttpActivity

![](http://stepflow-docs.cn-bj.ufileos.com/http001.png)

根据产品选择对应的UAPI，并填写入参值。
![](http://stepflow-docs.cn-bj.ufileos.com/uapi002.png)

对应的UAPI，输出的键值都已默认设置完成，用户无需额外操作，可以直接在之后的步骤中调用UAPI的出参。
![](http://stepflow-docs.cn-bj.ufileos.com/uhttp004.png)
