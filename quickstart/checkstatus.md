{{indexmenu_n>3}}

# 利用是非逻辑步骤构建循环用于查询任务状态

    创建一个主机的工作流并非只是调用一个创建接口，我们还需要利用到循环的方式检测主机状态是否启动，是否真正的创建正常。

以下流程会引起一台1C1G云主机的资费产生，请用户知晓。

## 第一步 创建一个命名空间

![](http://stepflow-docs.cn-bj.ufileos.com/createnamespace001.png)

命名空间命名规则：以小写字母或数字开头和结尾,包含小写字母,数字,-和\_,不超过16位

命名空间ID 为保证全局唯一性会在用户命名后增加6为随机码

![](http://stepflow-docs.cn-bj.ufileos.com/createnamespace002.png)

## 第二步 创建一个工作流

![](http://stepflow-docs.cn-bj.ufileos.com/createworkflow003.png)

工作流命名规则：以小写字母或数字开头和结尾,包含小写字母,数字,-和\_,不超过16位。

同一命名空间内，无法创建2个名称相同的工作流。

![](http://stepflow-docs.cn-bj.ufileos.com/createworkflow004.png)

## 第三步 调用创建主机的UAPI （CreateUHost）

括号内为步骤命名

选择“新增步骤”-“执行步骤”-“UHttpActivity”来创建一个UAPI服务。

第一次使用UHttpActivity服务时，会有短信验证获取用户的认证信息用于调用UCloud 的API。

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus001.png)

点击创建出的步骤并选择创建主机的接口“CreateUHostInstance”

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus002.png)

根据API
文档填写必填字段，<https://docs.ucloud.cn/api/uhost-api/create_uhost_instance>

我们选择北京二可用区E 1C1G数据盘

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus003.png)

备注：运行之前可以进行UAPI产品的测试。

## 第四步 判断创建接口是否正常 （CreateAPIOK）

使用“新增步骤”-“逻辑步骤”-“是非判断”来判断的是否“CreateUHostInstance” 正常执行。

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus004.png)

UCloud
API的返回值都有RetCode，通常我们用RetCode是否等于“0”来判断接口是否被执行正常。填写是非判断信息并点击“保存输入参数”

变量名称：用户自定义

变量取值语法：（需要调用其他步骤的出参值的话） ${步骤名.output.出参名称}

如图示：取值为 步骤名= CreateUHost 出参名称= RetCode 的值

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus005.png)

## 第五步 调用查询主机状态接口“DescribeUHostInstance” （GetUHostStatus，GetStatusAPIOK）

云主机创建任务完成后云主机并非直接可用，有一段时间的“初始化”状态，我们需要等到主机真正初始化完成后的状态方可使用。

步骤三 CreateUHostInstance 接口有默认出参 UHostIds 。由于是数组，我们取UHostIds. 0
用于将数组中的第一个元素，转化为STRING类型。

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus006.png)

“DescribeUHostInstance”接口入参 UHostIds.0 取值源于 步骤“CreateUHost” 的出参 根据语法：
${CreateUHost.output.UHostIds}

备注：我们需要取DescribeUHostInstance 返回值 UHostSet
内的State字段，我们可以在此步骤增加个出参帮助我们后续取值。

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus007.png)

语法： ${数组名.元素顺序(从0开始).参数名} UHostSet是个数组，取第一个元素中的State参数。

同样我们配上检查接口的步骤 ：一个是非逻辑步骤，可以命名为“GetStatusAPIOK”，依然用RetCode作为判断依据。

## 第五步 利用“是非判断”，“等待” 构建循环检查云主机是否创建成功。（StatusRunning，Wait）

创建一个“是非判断”命名为 “StatusRunning”用于判断状态是否为“Running”

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus008.png)

判断为GetUHostStatus的State出参值是否等于“Running” 。

如果成功，流程结束，

如果没有成功，指向“GetUHostStatus”步骤反复运行，为了避免过于频繁拉取接口需要给予一定的主动延时。

“新增步骤”-“逻辑步骤”-“等待” 等待默认为5秒的延迟。

效果：如果检测状态不是“Running”，间隔5秒继续进行检查。（可以扩展继续对失败的状态处理，这里暂且不展开）

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus009.png)

最终进行下流程的编排，流程示意如下：

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus010.png)

## 第五步 保存并执行工作流

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus011.png)

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus012.png)

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus013.png)

执行结果

![](http://stepflow-docs.cn-bj.ufileos.com/checkstatus014.png)

此流程没有编写失败，成功的通知机制，用户可以根据自己需求继续完善，例如添加USMS的短信服务。
