# 小米AX6000解锁ssh，刷机openwrt固件 clash翻墙，AX6000 科学上网
本教程解锁 AX6000 SSH 不需要借助其它软路由，教程有点长，请大家仔细看视频教程<br>
AX6000解锁SSH 视频教程：https://youtu.be/cLSEmZ6ufE4

#### 工具下载，<a href="https://github.com/kjfx/AX6000/releases/download/AX6000/AX6000-SSH.zip" target="_blank">点击下载>></a>

#### 第一步，设置 移动热点
网络名称改成：OpenWrt，密码：12345678 ，频带：2.4GHz<br>
查看WiFi信道（通常为1），可通过另外的电脑或手机APP连接这个WiFi查看信道。

#### 第二步，AX6000刷固件，降级

#### 第三步，安装VMware虚拟机，并安装OpenWrt
OpenWrt 地址：192.168.5.1    用户名：root   密码：password

#### 第四步，用WinSCP上传“xqsystem.lua”到OpenWrt的目录：/usr/lib/lua/luci/controller/admin/

#### 第五步，将OpenWrt LAN口 IPv4 改为：169.254.31.1

#### 第六步，开启 移动热点 ，并设置热点网络连接，去掉 Internet 协议版本 IPv4

#### 第七步，编辑虚拟机的桥接网络
编辑 > 虚拟网络编辑器 > 更改设置

#### 第八步，登录小米AX6000

    http://192.168.31.1/cgi-bin/luci/;stok=XXXXXX/api/xqsystem/extendwifi_connect_inited_router?ssid=OpenWrt&password=12345678&encryption=WPA2PSKenctype=CCMP&channel=1&band=2g&admin_username=root&admin_password=admin&admin_nonce=xxx

#### 第九步，通过SN获取默认root账号的密码（SN码在路由器底部或192.168.31.1 能查看到）

    https://miwifi.dev/ssh
    
*如果以上计算密码网址打不开，请下载这个使用，<a href="https://github.com/kjfx/AX6000/releases/download/AX6000/SN.zip" target="_blank">点击下载>></a> <br>
<code>SN码格式：30212/F1ZD22032</code><br><br>

## 常见问题：
**需要特别注意：<br>**
1、每次登录小米路由器后台 stok码 都会变动，请以最新登录的为准。<br>
2、解锁SSH成功之后有可能不会有任何提示，可以用putty登录查看是否解锁成功，显示“ARE U OK”就表示解锁成功。<br>
3、如果第一次没解锁成功，请重新登录小米路由器后台，再重新复制 stok码 ，再次解锁。<br><br>

**如果登录不了OpenWrt  192.168.5.1<br>**
1、重启一下OpenWrt，手动重启，或者输入命令：reboot<br>
2、首先确定OpenWrt的的IP是否改成了 169.254.31.1，改成了这个就要用这个IP登录<br>
3、将本地网络连接IP网段改为 OpenWrt IP 网段<br>
4、打开VMware：关闭正在运行虚拟机OpenWrt，编辑 > 虚拟网络编辑器 > 更改设置 > 还原默认设置<br>
5、在浏览器输入 OpenWrt IP 登录。<br><br>

**如果出现：{"msg":"一键换机过程中请求对端接口失败","code":1643}**<br>
在虚拟机中，输入：<br>
vim /etc/config/dhcp<br>
然后按住d键，删除全部内容，然后按 ESC 键<br>
再按":wq"<br>
再按回车键<br>
然后重启虚拟机，输入"reboot"<br>


# 安装ShellClash 科学上网
小米AX6000科学上网教程：https://youtu.be/vn5QdyDlTtI

    export url='https://fastly.jsdelivr.net/gh/juewuy/ShellCrash@master' && sh -c "$(curl -kfsSl $url/install.sh)" && source /etc/profile &> /dev/null
    
如果不能安装请使用下面备用安装源：

    #1
    export url='https://raw.githubusercontent.com/juewuy/ShellClash/master' && sh -c "$(curl -kfsSl $url/install.sh)" && source /etc/profile &> /dev/null

    #2
    export url='https://fastly.jsdelivr.net/gh/juewuy/ShellClash@master' && sh -c "$(curl -kfsSl $url/install.sh)" && source /etc/profile &> /dev/null

    #3
    export url='https://gh.jwsc.eu.org/master' && sh -c "$(curl -kfsSl $url/install.sh)" && source /etc/profile &> /dev/null

    #4
    export url='https://raw.githubusercontent.com/juewuy/ShellClash/master' && wget -q --no-check-certificate -O /tmp/install.sh $url/install.sh  && sh /tmp/install.sh && source /etc/profile &> /dev/null

    #5
    export url='https://fastly.jsdelivr.net/gh/juewuy/ShellClash@master' && wget -q --no-check-certificate -O /tmp/install.sh $url/install.sh  && sh /tmp/install.sh && source /etc/profile &> /dev/null

    #6
    export url='http://test.shellclash.cf' && wget -q -O /tmp/install.sh $url/install.sh  && sh /tmp/install.sh && source /etc/profile &> /dev/null

<br>


