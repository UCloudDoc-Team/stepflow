{{indexmenu_n>15}}

# Http步骤

Http步骤 HttpActivity作为工作流服务里执行外部服务的步骤。输出参数为对应外部服务返回参数。

## HttpActivity 示意图

![](http://stepflow-docs.cn-bj.ufileos.com/http002.png)

## HttpActivity 输入模版

    {
      "body": {
        "UserID": "${workflow.input.UserID}",
        "UserName": "${workflow.input.UserName}"   //入参定义， example为获取整体workflow的入参（UserID，UserName），具体参数定义请查看“通用”部分
      },
      "header": {
        "ContentType": "application/json"
      },
      "method": "GET",
      "query": {
        "Action": "VerifyUser"                   //请求action
      },
      "retrytimes": 0,
      "timeout": 0,
      "url": "http://mock.prj-hela.svc.a1.uae:8081?Action=VerifyUser"   //请求地址
    }

## 创建HttpActivity

![](http://stepflow-docs.cn-bj.ufileos.com/http001.png)
