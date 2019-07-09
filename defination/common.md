{{indexmenu_n>1}}

# 通用

工作流服务 StepFlow 含有自己对微服务I进行编排的语法，定义需要用户了解。

## 参数定义

参数分为步骤参数 和 工作流参数

工作流参数：工作流运作时所需要传入的参数，和整体工作流运行完所获取的出参

步骤参数：对于单步骤设定的参数

当前步骤出参值：${变量名} 例如： ${RetCode}

获取指定步骤入参值：${步骤名.input.变量名} 例如： ${step001.input.UserName} or
${workflow.input.UserName} (整个workflow的入参value)

获取指定步骤出参出产：${步骤名.output.变量名} 例如： ${step001.output.UserName} or
${end.output.UserName} (整个workflow的出参value)
