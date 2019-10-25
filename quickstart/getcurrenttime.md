

# 调用一个查询当前时间的外部服务

## 第一步 创建一个命名空间

![](http://stepflow-docs.cn-bj.ufileos.com/createnamespace001.png)

命名空间命名规则：以小写字母或数字开头和结尾,包含小写字母,数字,-和\_,不超过16位

命名空间ID 为保证全局唯一性会在用户命名后增加6位随机码

![](http://stepflow-docs.cn-bj.ufileos.com/createnamespace002.png)

## 第二步 创建一个工作流

![](http://stepflow-docs.cn-bj.ufileos.com/createworkflow003.png)

工作流命名规则：以小写字母或数字开头和结尾,包含小写字母,数字,-和\_,不超过16位。

同一命名空间内，无法创建2个名称相同的工作流。

![](http://stepflow-docs.cn-bj.ufileos.com/createworkflow004.png)

## 第三步 创建一个Http步骤

选择“新增步骤” - “执行步骤” - “HttpActivity”

![](http://stepflow-docs.cn-bj.ufileos.com/http001.png)

点开步骤修改步骤名为“GetCurrentTime”

![](http://stepflow-docs.cn-bj.ufileos.com/getcurrenttime001.png)

这次所使用的外部服务信息：

请求: worldclockapi.com/api/json/est/now

返回值：

``` 
{
"$id": "1",
"currentDateTime": "2019-06-18T04:49-04:00",
"utcOffset": "-04:00:00",
"isDayLightSavingsTime": true,
"dayOfTheWeek": "Tuesday",
"timeZoneName": "Eastern Standard Time",
"currentFileTime": 132053069942472210,
"ordinalDate": "2019-169",
"serviceResponse": null
}

```

备注：目前仅支持对于json格式返回值的解析。

由上述返回值可得，我们需要取的字段为“currentDateTime”

首先对HttpActivity的输如参数部分进行编辑，内容如下：

    {
    "body": {},
    "header": {
    "ContentType": "application/json"
    },
    "isAsync": false,
    "method": "GET",
    "query": {},
    "retrytimes": 0,
    "timeout": 0,
    "url": "http://worldclockapi.com/api/json/est/now"
    }

点击HttpActivity步骤的“保存输入参数”

对HttpActivity的输出参数进行取值定义。

![](http://stepflow-docs.cn-bj.ufileos.com/getcurrenttime003.png)

名称 定为 CurrentTime 用户可自定义出参名。

类型 选择 STRING

值 填写 ${currentDateTime} 语法： $ + 大括号 + 请求返回参数名

如：希望输出“星期几”可以根据请求返回值填写 名称：Day 类型：STRING 值 ：${dayOfTheWeek}

将start HttpActivity end通过每个步骤的“后续步骤”编排成一个工作流，如图：

![](http://stepflow-docs.cn-bj.ufileos.com/getcurrenttime002.png)

## 第四步 保存工作流并运行

![](http://stepflow-docs.cn-bj.ufileos.com/runtime001.png)

![](http://stepflow-docs.cn-bj.ufileos.com/runtime002.png)

![](http://stepflow-docs.cn-bj.ufileos.com/runtime003.png)

由于此工作流没有工作流入参需要填写，所以运行工作流界面没有需要额外填写的内容。

## 第五步 查看执行结果

运行完工作流会页面会跳转到运行轨迹页面。

如工作流仍在运行用户可使用流程画布右上角的刷新按钮查看执行的最新状态。

![](http://stepflow-docs.cn-bj.ufileos.com/checktime001.png)

待工作流执行完成后可以点击“GetCurrentTime”步骤查看输出结果。

![](http://stepflow-docs.cn-bj.ufileos.com/checktime002.png)
