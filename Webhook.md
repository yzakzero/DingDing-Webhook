# 一、钉钉定时群发机器人案例简介

最近因特殊情况要求，需要每日定时群发大量信息，且该信息的内容每日均有所不同。目前这项工作依靠人工进行，然而该项工作的工作量就目前而言已超出人工所能处理的范围，因此想借用钉钉Webhook自定义机器人来代替人工处理这项工作。利用已封装好的包，可以直接使用python进行编写。
# 二、相关参考链接：
### Webhook机器人
1. [Webhook官方文档](https://ding-doc.dingtalk.com/doc#/serverapi2/qf2nxq) 

### Python
1. [DingtalkChatbot:Python封装库](https://github.com/yzakzero/DingtalkChatbot)
2. [schedule 任务调度库](https://www.cnblogs.com/wanglinjie/p/9286338.html)
3. [PyCharm安装及使用](https://blog.csdn.net/qq_40130759/article/details/79421242)
4. [time库](https://www.runoob.com/python/python-date-time.html)
### FinalShell
1. [Mac os环境安装](https://blog.csdn.net/iamlihongwei/article/details/96835576)
2. [设置相关](https://jingyan.baidu.com/article/11c17a2cfff2eaf447e39d7c.html)

### Linux
1. [pip安装](https://www.cnblogs.com/zhongyehai/p/10619917.html)
2. [后台挂载/卸载](https://blog.csdn.net/yongh701/article/details/78378041)
3. [系统当前时间获取](https://blog.csdn.net/m0_37556444/article/details/82910532)

# 三、执行所需环境
#### Macos,Linux,Finalshell,PycharmCE,钉钉桌面端

# 四、注意事项
### curl命令
一定要严格按照官方文档，将测试语句直接粘贴至控制台，然后复制对应的taken至‘=’后，否则有极大可能发生错误。




### 时间同步
1. 使用了time.strftime("%m月%d日",time.localtime(time.time()))
2. 未把时间参数放置def内
```markdown
import datetime
from dingtalkchatbot.chatbot import DingtalkChatbot
import time
import schedule

#wehook地址
webhook = 'https://oapi.dingtalk.com/robot/send?access_token=xxx'
#机器人初始化
xiaoding = DingtalkChatbot(webhook)
#datetime.now获取实时时间 time库只获取当前时间
s = datetime.datetime.now().second

def job1():
  msg1=s.__str__()
  xiaoding.send_text(msg1, is_at_all=1)

#时间未刷新
```
### 添加新的推送信息忘记在校验添加条件
在程序内部新建一条新语句时，应有限考虑

### 同一定时任务未放在同一函数里进行编写


### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```
# 五、实现过程

