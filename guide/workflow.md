{{indexmenu_n>20}}

# 工作流

## 创建工作流

根据提示填写workflow命名

![](http://stepflow-docs.cn-bj.ufileos.com/createwf001.png)

![](http://stepflow-docs.cn-bj.ufileos.com/savewf001.png)

备注：

1 创建至保存过后才算创建成功，保存之前如网页刷新StepFlow将不会记录之前编辑中状态。

2 保存时会做工作流语法校验，如有报错请根据保存时的提示检查工作流定义。

## 修改工作流备注

![](http://stepflow-docs.cn-bj.ufileos.com/wfremark.png)

## 删除工作流

![](http://stepflow-docs.cn-bj.ufileos.com/deletewf001.png)

备注：当需要批量删除工作流可以选中多个目标后使用左上方的“删除工作流”

## 运行工作流

![](http://stepflow-docs.cn-bj.ufileos.com/run001.png)

![](http://stepflow-docs.cn-bj.ufileos.com/run002.png)

备注：

1 只有保存过后的工作流可以运行，编辑过后的工作流需要保存后才能继续运行。

2 运行界面格式为json，前端会对格式进行校验，如不符合json规范则无法执行。

## 导出工作流定义

点击“导出工作流定义”按钮后，会展示具体定义，并能够将当前界面版本的工作流定义进行复制导出。

![](http://stepflow-docs.cn-bj.ufileos.com/export001.png)

![](http://stepflow-docs.cn-bj.ufileos.com/export002.png)

## 导入工作流定义

导入的工作流名称如果在当前namespace下已存在，则为该工作流生成新的版本。如无，即创建了一个全新的工作流。

![](http://stepflow-docs.cn-bj.ufileos.com/import001.png)

![](http://stepflow-docs.cn-bj.ufileos.com/import002.png)


## 切换/发布工作流版本

工作流提供版本管理，发布后的版本为外部调用和进入工作流的默认版本，也可以手动切换版本运行当前版本工作流。

![](http://stepflow-docs.cn-bj.ufileos.com/version001.png)
