

# 创建云主机并绑定ULB

【addulbrserver】创建一台云主机（配置可调整）并绑定到用户已有的ULB Vserver。

## 主要流程

创建云主机（预配置，模板中使用了2C4G）

检测创建云主机接口是否正常

反复检测云主机状态是否为“运行”

绑定用户ULB Vserver（预配置）

检测绑定接口是否成功

## 输入输出定义

工作流输入

| 参数名       | 类型   | 描述                          |
| ------------ | ------ | ----------------------------- |
| ULBId        | STRING | ULB ID 如:ulb-xxxx             |
| VserverId    | STRING | Vserver ID 如:vserver-xxxxx |
| ListenerPort | INT64  | 监听端口 如:1001               |
| Region       | STRING | 区域名 如:cn-bj2               |
| Zone         | STRING | 可用区名 如:cn-bj2-05         |


工作流输出

| 参数名       | 类型   | 描述                          |
| ------------ | ------ | ----------------------------- |
| UHostId        | STRING | UHost ID 如：uhost-xxxx           |
| CreateErrMessage    | STRING | 创建云主机接口错误信息 |
| GetErrMessage | STRING  | 获取云主机状态接口错误信息               |
| AllocateErrMessage | STRING | 绑定ULB Vserver错误信息               |

## 使用方法

选择对应的模板创建工作流

![](http://stepflow-docs.cn-bj.ufileos.com/sample001.png)
