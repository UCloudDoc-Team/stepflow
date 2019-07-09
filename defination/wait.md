{{indexmenu_n>26}}

# 等待逻辑

为避免微服务间由于停留过短造成运行异常，stepflow提供了WaitDecision让用户主动控制微服务间的延迟。

## WaitDecision 输入

![](http://stepflow-docs.cn-bj.ufileos.com/wait.png)

delay：延时时长，单位s。

备注：

1 默认时间为5s，delay支持延时时长需要大于5s。

2 支持输入变量，如${step001.output.param}，变量需要是INT64类型。
