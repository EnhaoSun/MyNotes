Deep-Wine GitHub: https://github.com/wszqkzqk/deepin-wine-ubuntu

# 微信
版本选择：

https://gitee.com/wszqkzqk/deepin-wine-containers-for-ubuntu/raw/master/deepin.com.wechat_2.6.8.65deepin0_i386.deb

## 中文字体解决
**解决方法： https://github.com/wszqkzqk/deepin-wine-ubuntu/issues/136#issuecomment-514585722**

下载微软雅黑字体,msyh.ttc: 

* https://github.com/owent-utils/font/blob/master/%E5%BE%AE%E8%BD%AF%E9%9B%85%E9%BB%91/MSYH.TTC

```shell
#1.添加字体
cp msyh.ttc ~/.deepinwine/Deepin-WeChat/drive_c/windows/Fonts

#2.修改系统注册表
gedit ~/.deepinwine/Deepin-WeChat/system.reg
#修改以下两行
"MS Shell Dlg"="msyh"
"MS Shell Dlg 2"="msyh"

#3.字体注册
gedit msyh_config.reg
#内容添加
REGEDIT4
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\FontLink\SystemLink]
"Lucida Sans Unicode"="msyh.ttc"
"Microsoft Sans Serif"="msyh.ttc"
"MS Sans Serif"="msyh.ttc"
"Tahoma"="msyh.ttc"
"Tahoma Bold"="msyhbd.ttc"
"msyh"="msyh.ttc"
"Arial"="msyh.ttc"
"Arial Black"="msyh.ttc"
#注册
WINEPREFIX=~/.deepinwine/Deepin-WeChat deepin-wine regedit msyh_config.reg

#4.reboot

```
