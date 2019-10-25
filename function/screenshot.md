

# 截图任务

截图任务 功能使用UMedia，UFile产品，将用户希望截图的视频地址转码成需要的格式并上传至UFile的空间。

# 输入定义

FileUrl：视频URL

SnapType：截图模式，single表示确定时间点单张截图，periodic表示周期截图, dynamic表示为gif截图

SnapTime：截图模式为single时表示截图时间点，periodic时表示时间间隔

DestBucket：UFile空间名

ImageFormat：图片类型，支持jpg、png、gif

# 输出定义

RetCode：返回码

Status：任务状态

TaskId：任务ID

# 使用方法

![](http://stepflow-docs.cn-bj.ufileos.com/function001.png)
