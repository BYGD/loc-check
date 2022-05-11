# loc-check
 hostloc.com签到Python版，添加server酱推送，每日领取20分

宝塔部署Hostloc论坛自动签到Python脚本（增加server酱推送）图文教程：
https://www.idonglei.com/post/612.html 





## 小鸡定时获取hostloc积分

github action大规模失效，mjj平均一人10鸡，以下可以部署到自己的小鸡上

**第一步**下载下列代码

方法1： 【建议】下载到本地进行修改：
```shell
https://github.com/DocWho22/hostloc_getPoints/blob/main/hostloc_auto_get_points.py
```

方法2：直接下载到服务器
```shell
wget -p /root/hostloc https://raw.githubusercontent.com/DocWho22/hostloc_getPoints/main/hostloc_auto_get_points.py
```


**第二步**在209, 210, 211行代码处添加你的用户名、密码、serverChan的SendKey
如果是在小鸡上进行修改
```shell
vim /root/hostloc/hostloc_auto_get_points.py
```
修改这几行
```python3
username = "在此填入用户名"
password = "在此填入密码"
serverChan = "在此填入Server酱SendKey"
```

**第三步**上面文件上传到小鸡

**第四步**在小鸡里新建crontab任务

```
crontab -e
```


添加

```shell
10 2 * * * sleep 5;python3 /root/hostloc/hostloc_auto_get_points.py
```

/root/hostloc/为你上传的路径
/usr/local/bin/python3为你小鸡python3的引用路径

**提示**

1.如果提示以下错误

```python
Traceback (most recent call last):
  File "/root/hostloc/hostloc_auto_get_points.py", line 6, in
   ...
```

请安装request模块

```shell
pip3 install requests
```

2.老哥们可先运行成功以后再添加crontab任务

```shell
python3 /root/hostloc/hostloc_auto_get_points.py
```



env
HOSTLOC_USERNAME=username1,username2...
HOSTLOC_PASSWORD=password1,password2...

## Credits
原作者：https://github.com/Jox2018/hostloc_getPoints
在原作者基础上增加了serverChan推送功能
fork自：https://github.com/DocWho22/hostloc_getPoints
