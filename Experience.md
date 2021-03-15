# 零散的经验

## Mac 使用 Surge 的技巧

### 增强模式分享代理给其他设备时

1. Mac 自身网络的 IPv4 获取设定为 Using DHCP with manual address, 并手动输入一个实体路由器中未被占用的地址
2. 其他设备连接实体路由器，配置 IPv4 为手动，输入一个实体路由器中未被占用的地址，子网掩码写 255.255.255.0, **路由器写 Mac IPv4 地址**
3. 配置 DNS 选择手动，DNS 服务器写 **198.18.0.2**, 这是 Surge 打开增强模式设定的 DNS 服务器，可在 Mac 端网络查看 DNS 得到。

### git clone ssh_address

ssh config 无需特殊配置即可使用。

## AOC 屏幕

选择 DisplayHDR 模式

## ClashX 问题

* [小白使用clashx连接线路出现问题，几乎全都是失败](https://github.com/yichengchen/clashX/issues/473), 是的，修改dns enable：false或者fallback里面添加8.8.8.8后就可以了

## [Mac iterm2 cheatsheet](https://gist.github.com/moqimoqidea/7512257f11a5342eb4df906964433d28)

## Mac 使用罗技键盘启动 Screen saver

参考 [3 ways to create a screen saver shortcut on Mac](https://www.idownloadblog.com/2020/02/06/create-screen-saver-shortcut-mac/) 里面的第二种方法。

## Mac WiFi 连接公司网络频繁中断

* 尝试 [重置 SMC](https://support.apple.com/zh-cn/HT201295), 无效；
* 在手机 APP 苹果支持里选择网络让苹果回电，客服建议 [新建网络位置](https://support.apple.com/zh-cn/HT202480), 随便写一个名字，目前有效，不咋中断。

## [Mac 调整通知内容到主屏幕](https://eshop.macsales.com/blog/59320-how-to-move-notifications-from-one-monitor-to-another-on-a-mac/)

在设置中心屏幕界面，拖拽白条到主要使用的屏幕。

## 使用 Git LFS 管理大文件

* [Github: Git LFS Repo](https://github.com/git-lfs/git-lfs)
* [Gitee: Git LFS 操作指南](https://gitee.com/help/articles/4235)

## [Git 如何提高 Github 的 pull/push 速度](https://ruby-china.org/topics/40408)

1. SSH type, edit ~/.ssh/config and append:

```
Host github.com *.github.com
    ProxyCommand nc -v -x 127.0.0.1:6152 %h %p
    HostName github.com
    User git

Host gitlab.com *.gitlab.com
    ProxyCommand nc -v -x 127.0.0.1:6152 %h %p
    HostName gitlab.com
    User git
```

2. HTTP type, edit ~/.gitconfig and append:

```
# proxy for github
[http "https://github.com"]
    proxy = http://127.0.0.1:6152
    sslVerify = false
# proxy for gitlab
[http "https://gitlab.com"]
    proxy = http://127.0.0.1:6152
    sslVerify = false
```

## 获取中文字符的 URI 编码

* 访问网页获得: [在线编码转换 URL 转码](https://tool.oschina.net/encode?type=4)
* 使用 js 代码获得: Chrome 打开任意网页控制台，输入 encodeURI('中文材料')
* 理论参考: [关于URL编码](http://www.ruanyifeng.com/blog/2010/02/url_encoding.html)

## [外接显示器时，让 Alfred 在当前显示器中显示](http://freelancer-x.com/196/%E5%A4%96%E6%8E%A5%E6%98%BE%E7%A4%BA%E5%99%A8%E6%97%B6%EF%BC%8C%E8%AE%A9-alfred-%E5%9C%A8%E5%BD%93%E5%89%8D%E6%98%BE%E7%A4%BA%E5%99%A8%E4%B8%AD%E6%98%BE%E7%A4%BA%EF%BC%88%E6%89%93%E5%BC%80%EF%BC%89/)

Preferencet-> Appearance -> Options -> Show Alfred on, choose mouse screen.

## [解决罗技 mx master3 鼠标按住控制键无法切换 Mac 桌面的问题](https://apple.stackexchange.com/a/310741)

鼠标调用的是键盘快捷键 Ctrl + <- / Ctrl + ->，因此需要在键盘设置中打开这对快捷键组合。

System Preferences -> Keyboard -> SHortcuts(top) -> Mission COntrol (left panel) -> Move left a space / Move right a space (right panel)

又因为鼠标操作与按键交互直觉上方向相反，因而把 Move left a space 设置为 Ctrl + ->, 把 Move right a space 设置为 Ctrl + <-, 直觉上比较匹配。

## Mac 为 APP 单独设定语言

Language & Region -> Apps: Customize language settings for the apps below.

## [解决 Mac OS X 中的蓝牙无线问题](https://support.logi.com/hc/zh-cn/articles/360023195654)

* [解决由无线干扰引起的 Wi-Fi 和蓝牙问题](https://support.apple.com/zh-cn/HT201542)
* [MacBook Pro2019款升级系统后连接蓝牙键盘不稳定的问题](https://discussionschinese.apple.com/thread/251456400)
* [Mos](https://mos.caldis.me/), 一个用于在 MacOS 上平滑你的鼠标滚动效果或单独设置滚动方向的小工具, 让你的滚轮爽如触控板。

## Mac 键盘输入温度的°符号

按下「shift + option + 数字 8」键，此方法会输出一个大一点的圆点「°」

## 使用 Pandoc 将 markdown 项目转换为 epub

* [Creating an ebook with pandoc](https://pandoc.org/epub.html)

## 使用 pyenv 管理 python 版本

* [Pyenv Github](https://github.com/pyenv/pyenv)
* [Pyenv Tutorial](https://realpython.com/intro-to-pyenv/)
* ERROR: The Python zlib extension was not compiled. Missing the zlib?  解决方案: xcode-select --install
* BUILD FAILED (OS X 11.0.1 using python-build 20180424)
  * CFLAGS="-I$(brew --prefix openssl)/include -I$(brew --prefix bzip2)/include -I$(brew --prefix readline)/include -I$(xcrun --show-sdk-path)/usr/include" LDFLAGS="-L$(brew --prefix openssl)/lib -L$(brew --prefix readline)/lib -L$(brew --prefix zlib)/lib -L$(brew --prefix bzip2)/lib" pyenv install --patch 3.6.12 < <(curl -sSL https://github.com/python/cpython/commit/8ea6353.patch\?full_index\=1)
  * [Unable to build Python on macOS Big Sur with Xcode 12 beta ](https://github.com/pyenv/pyenv/issues/1643#issuecomment-655710632)
  * [Python cannot be installed on Mac OS 11.0.1 pyenv](https://github.com/pyenv/pyenv/issues/1737#issuecomment-738080459)
  * [issue 1738](https://github.com/pyenv/pyenv/issues/1738), 需要在 [apple develop](https://developer.apple.com/download/more/) 下载 Command Line Tools for Xcode 12.3 Release Candidate. 
  * [pyenv installでエラーが発生する](https://medium.com/@bj1024/pyenv-install-error-mac-dcbd28fdc9db).
  

## Mac set allow apps downloaded from anywhere

```shell
sudo spctl --master-disable
```

## [更改 macOS 用户帐户和个人文件夹的名称](https://support.apple.com/zh-cn/HT201548)

## Mac 可以使用密码解锁，但是无法使用密码解锁 Security & Privacy

解决方案：重置 SMC，参考[If System Preferences doesn't accept a valid administrator password when you click the lock to make changes](https://support.apple.com/en-us/HT203127)

If System Preferences doesn't accept a valid administrator password when you click the lock to make changes, try these solutions.

Your Mac asks you to enter the name and password of an admin account when it needs to verify that you have permission to make changes. For example, you must authenticate as an administrator when you click the lock  in System Preferences, enter certain commands in Terminal, or set a firmware password.

System Preferences might not accept a valid password in these circumstances:

* The password for your macOS user account is blank. If you have been using a blank password to log in to your Mac, change your password in Users & Groups preferences. Don't use a blank password.

* While using macOS Big Sur 11.1, your Mac with Apple T2 Security Chip has an issue that requires resetting the SMC. System Preferences should accept your password after you reset the SMC.


## Mac 设置一位数密码

终端输入 pwpolicy -clearaccountpolicies , 然后会出现 Clearing global account policies 即表示成功，去掉了密码必须四位数的限制。

## [在 Mac 下找出监听某个 tcp 端口的程序](https://stackoverflow.com/a/4421674)

```shell
lsof -nP -iTCP:$PORT | grep LISTEN
```

## [在 Mac 下安装 gvm 管理 go 版本](https://github.com/moovweb/gvm)

## [在 Mac 下安装 nvm 管理 node 版本](https://blog.csdn.net/Charissa2017/article/details/104497572)

[nvm on github](https://github.com/nvm-sh/nvm)

## [在 Mac 下运行 Lisp 程序](https://luciaca.cn/2019/03/22/running-lisp-under-mac-os/)

1. brew install mit-scheme
2. 运行 REPL: mit-scheme
3. 运行代码文件: scheme < FILENAME

## [Mac OS python2 安装 pip 工具](https://stackoverflow.com/a/18947390)

1. curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
2. python get-pip.py

## Mac OS 更新到 Big Sur 版本之后 JD-GUI 无法使用

参考 [BigSur ERROR launching 'JD-GUI'](https://github.com/java-decompiler/jd-gui/issues/332), 把 JD-GUI 包文件中 /Applications/JD-GUI.app/Contents/MacOS/universalJavaApplicationStub.sh 的 JAVACMD 固定为 JAVACMD="/Library/Java/JavaVirtualMachines/jdk1.8.0_261.jdk/Contents/Home/bin/java" 的格式，去掉 # first check system variable "$JAVA_HOME" 中冗余的 JAVACMD 判断。

## Mac OS 更新到 Big Sur 版本之后随航功能无法使用

在 iPad 上退出 iCloud 并重新登陆，然后在 Mac 的系统设置中更新 Apple ID 的信息，需要输入 iPad 的锁屏密码，最终可以正常使用。参考[Sidecar not working on Big Sur and iPad OS](https://discussions.apple.com/thread/252042262).

## Mac OS 更新到 Big Sur 版本之后使用随航连接 iPad 显示 timeout

Make sure that Handoff is not checked on both the iPad and the Mac. To Disable Handoff on your devices:

* iPad, iPhone, and iPod touch: Go to Settings , then tap General > Handoff.
* Mac: Choose Apple Menu > System Preferences > General, then turn off “Allow Handoff between this Mac and your iCloud devices.”

From: Support.Apple, 参考["Device Timed Out" error in Sidecar](https://discussions.apple.com/thread/250715445)

## homebrew through proxy

ALL_PROXY=http://127.0.0.1:6152 brew upgrade
参考: [Homebrew behind proxy](https://github.com/Homebrew/legacy-homebrew/issues/11114#issuecomment-62933075)

## the mercurial clone through proxy

http_proxy=http://proxy-server:8080 hg clone https://vim.googlecode.com/hg
参考: [To use proxy for Mercurial you can prefix your command with http_proxy](https://stackoverflow.com/a/35941669)

## Mac 上的十六进制文件编辑器

[Hex Fiend](https://ridiculousfish.com/hexfiend/)