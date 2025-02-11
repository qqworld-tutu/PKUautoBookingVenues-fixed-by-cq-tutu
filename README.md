# PKU AutoBookingVenues -fixed by cq-tutu
PKU智慧场馆自动预约工具

部分代码和这个README的一部分引用自之前的智慧场馆自动预约项目 https://github.com/Charliecwei/PKU_Venues_Auto_Book

本羽毛球鼠鼠想打羽毛球一直抢不到场啊！于是便萌生了自动预约场地的想法。在github上找到了之前大佬写的程序。然而，年久失修的代码如今已经完全无法运行。因此，本项目在之前项目的基础上进行了较大修改，主要体现在以下三个方面：

1. selenium库更新了，之前的语法已经无法跑通
2. 智慧场馆网站也新写了，许多爬虫代码也随之修改
3. 提交预约时的验证方式改成了文字点击，于是使用了超级鹰的api来识别



> [!CAUTION]
>
> 本项目还在初期阶段，各方面都不甚完善，如有任何意见或建议，欢迎联系我。（wechat：dj7152，email：chenquan@stu.pku.edu.cn）




## 说明

- 本工具采用 Python3 搭配 `selenium` 完成自动化操作，实现全自动预约场馆
- 本项目需要提前安装firefox浏览器以及驱动，请把firefox驱动复制到该文件夹下
- 支持基于[Server酱](https://sct.ftqq.com/)的备案结果微信推送功能，体验更佳
- 采用定时任务可实现定期（如每周）免打扰预约，请设置在三天前的11:55-12:00之间
- 第三方依赖包几乎只有 `selenium` 一个
- 由于我只测试过羽毛球场的预约，其他场馆只是理论上可行，如果出现任何问题，可以提issue
- 目前仅支持一个小时的预约，后续可能会增加两个小时预约的功能
- `config`参数填写`config.ini`文件的名称，类型为字符串
- `lst_config`为config文件名称字符串构成的列表
- `page(config)`单独处理每个`config.ini`文件,`muilti_run(lst_config)`并行处理`lst_config`列表中的所有`config.ini`，`sequence_run(lst_config)`按序处理
- 定时任务还未经过完全测试
- 注意付款需要手动执行！请在10分钟内自行完成付款！




## 安装与需求

### Python 3

本项目需要 Python 3，可以从[Python 官网](https://www.python.org/)下载安装

### Packages

#### selenium

采用如下命令安装 `selenium`，支持 selenium 4 及以上版本：

```python
pip install selenium
```

### API

#### 超级鹰

在https://www.chaojiying.com/注册，并充钱（最少充10块钱，可识别验证码625次）

然后，进入用户中心，在左侧菜单栏中点击“软件ID”，生成一个软件ID，并填入config文件中的soft_id



## 基本用法

1. 将 `config.sample.ini` 文件重命名为 `config0.ini` ，如果需要多个账号预约，或者需要时间上的“与”关系，请设置多个.ini文件（最多为两位数），
   请不要新建文件，不然自己搞定编码问题

2. 用文本编辑器（建议代码编辑器）打开 `config0.ini` 文件

3. 配置 `[login]` 、`[type]` 、`[time]`、`[wechat_notice]` 、`[chaojiying`]这几个 Section 下的变量，在 `config0.ini.sample` 文件内有详细注释


## 定时运行

### Windows

本项目中的 `autoRun.bat` 文件可提供在静默免打扰情况下运行程序的选择，配合 Windows 任务计划管理可实现定期自动填报，具体请参考[Win10下定时启动程序或脚本](https://blog.csdn.net/xielifu/article/details/81016220)

### mac OS

进入项目根目录，以命令 `./macAutoRun.sh` 执行 `macAutoRun.sh` 脚本即可，可设定或取消定时运行

### Linux

使用 `crontab` 设置

**Note:** 静默运行的弊端为无法看到任何报错信息，若程序运行有错误，使用者很难得知。故建议采用定时静默运行时，设置微信推送，在移动端即可查看到备案成功信息。



## 微信推送

本项目支持基于[Server酱](https://sct.ftqq.com/)的微信推送功能，仅需登录并扫码绑定，之后将获取到的 SCKEY 填入 `config0.ini` 文件即可



## 责任须知

- 本项目仅供参考学习，造成的一切后果由使用者自行承担



## 证书

[Apache License 2.0](https://github.com/yanyuandaxia/PKUAutoBookingVenues/blob/main/LICENSE)



## 版本历史
### version 1.0

- 发布于 2025.2.9
- 项目初始版本
