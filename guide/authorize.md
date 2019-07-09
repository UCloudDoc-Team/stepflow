{{indexmenu_n>25}}

# UToken授权

为了让工作流编辑者可以分享自己编写的工作流给其他用户使用，我们接入了UToken授权，让任何一个外网用户可以根据授权调用工作流。

调用工作流会给编辑者带来费用例如工作流自身的调用费用，和UCloud资源费用（如调用包含购买行为的工作流）等，请用户知晓。

## 创建授权用户组

用户组作为授权的分类依据，用户可以自定义作为标识。

![](http://stepflow-docs.cn-bj.ufileos.com/authorize001.png)

根据提示填写用户组信息

![](http://stepflow-docs.cn-bj.ufileos.com/authorize002.png)

## 创建UToken

选择用户组

![](http://stepflow-docs.cn-bj.ufileos.com/authorize003.png)

点击“管理令牌”

![](http://stepflow-docs.cn-bj.ufileos.com/authorize004.png)

点击“创建令牌”

![](http://stepflow-docs.cn-bj.ufileos.com/authorize005.png)

根据需求填写授权时效，并获取token码

![](http://stepflow-docs.cn-bj.ufileos.com/authorize006.png)

![](http://stepflow-docs.cn-bj.ufileos.com/authorize007.png)

## 外部调用workflow

进入workflow编辑页面，根据url地址进行调用

例：

curl -X POST
'<https://stepflow.ucloud.cn/namespace/namespaceID/workflow/workflowname/version/0?cid=companyid&token=yourtoken>'
-H 'Content-Type: application/json; charset=utf-8' -d

'{

*workfolow入参json格式*

}'

备注： yourtoken= token码 companyid=公司id（非邮箱）

![](http://stepflow-docs.cn-bj.ufileos.com/authorize008.png)
