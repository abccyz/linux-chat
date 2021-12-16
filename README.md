# Wine安装原版企业微信教程(非deepin版本)

> linux-tencent

> linux 下非deepin的企业微信和微信安装方法

 
> 前言：之前使用wine封装的`QQ`或者微信亦或者是企业微信使用起来总是不爽，所以尝试自行安装`wine`然后再安装`win`下的应用,本篇文章理论适应所有的`Windows`的应用.
>
> ​	`Ubuntu`上有几个基于`Wine`封装的企业微信，但是版本都是比较老的(功能也不是很好用)，个人是比较习惯使用比较新的软件，所以就有了以下的尝试，到目前企业微信运行的还不是很完美，存在一些问题(具体问题后面补充)。
>
> ​	本篇文章的目的让喜欢使用linux系统的朋友们不必再因为选择了linux后无法使用办公软件的而产生烦恼。(linux真的很棒!!!)

**正常功能(操作顺畅)**

- 消息发送
- 表情发送
- 语音电话
- 历史消息
- 搜索
- 图片发送
- 代码
- 微文档
- 群工具
- 远程控制

**异常功能：**

- 截图(有其他方案代替)

> 因为是基于原版`wine`所以可以跟随官方更新 ！！！

先欣赏下效果：
 ![image.png](https://upload-images.jianshu.io/upload_images/4652214-c96d2d0ac6da5bf6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 

## 准备

###  推荐大家这个基于Ubuntu18的[ElementaryOS](https://elementary.io)
<strong >`台式机或笔记本内存较小用户的福音`</strong>
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200525095120121.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiY2N5eg==,size_16,color_FFFFFF,t_70)
- 看看我的8G内存在这个系统上表现
![资源占用](https://img-blog.csdnimg.cn/20200525095328264.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiY2N5eg==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020052509555849.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FiY2N5eg==,size_16,color_FFFFFF,t_70)
> 我设置了12G的交换分区，物理内存使用达到90%以上，系统依然是流畅，不会有任何卡顿【日常开4个IDEA  浏览器开20个以上标签,还有企业微信，微信和其他的常用工具。用黑苹果和win10 开2个就会卡顿到不能正常操作】--> 这个也是我选择linux的原因 :)




- ElementaryOS5.1 (我用的就是这个下图，不知道的可以参考：https://elementary.io)

   ![系统信息](https://upload-images.jianshu.io/upload_images/4652214-1cf51b089b609cc6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 安装Wine5.0  (5.0是稳定版/5.7是开发版我的机器安装的5.0， 提示下:下不动的可以尝试用手机网络+fanqiang,官网链接: https://www.winehq.org)
   - 如果已经安装确认下版本，方法如下：
    ![查看wine版本](https://upload-images.jianshu.io/upload_images/4652214-43d0735d8d76ff21.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   
- `winetricks`是`wine`辅助工具(不一定用，我习惯用命令行)，具体安装可以参考：https://github.com/Winetricks/winetricks

- 企业微信官网安装包(自行到企业微信官网下载最新，官网连接：https://work.weixin.qq.com)

## 安装过程

### Wine安装

1. `sudo apt-cache search wine` 搜索是否存在`wine`,输入密码开始搜索

2. 搜索结果，选择`wine-stable`

   ![搜索wine.png](https://upload-images.jianshu.io/upload_images/4652214-467e9c72bb1e1a91.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 执行`sudo apt-get install wine-stable `

   ![wine-stable](https://upload-images.jianshu.io/upload_images/4652214-5ba8fa2c6509e43f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. 验证安装结果，输入 `wine --version`

    ![wine-version](https://upload-images.jianshu.io/upload_images/4652214-f79a540be53adb5a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

​		果然版本是比较老的。

5. 安装`winetricks`,输入`sudo apt-cache search winetricks`

   ​	![winetricks](https://upload-images.jianshu.io/upload_images/4652214-b1f125f64b43c3a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6. 执行安装 `winestricks`,输入`sudo apt-get install winetricks`

   ![image-20200430095057374.png](https://upload-images.jianshu.io/upload_images/4652214-c0a4996927a3ac80.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   完成安装。

7.  解决输入框不显示输入内容,将准备好的`W2KSP4_EN.EXE`放到`/home/你的账户名/.cache/winetricks/win2ksp4/`下载，执行 `winetricks riched20`(过程中还会下载几个文件那据无关紧要的文件都是比较小的很快的)

   ![按转dll](https://upload-images.jianshu.io/upload_images/4652214-124ce9bee4346c58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

8. 执行`wine WXWork_3.0.16.1614.exe`(去企业微信官网下载最新的包)，等了很久没反映(应该是wine的版本太老了)这里就终止了，不等了升级`wine`去. 终止时看到问题是：

   ```bash
   002f:err:ntdll:RtlpWaitForCriticalSection section 0x7bce56c0 "loader.c: loader_section" wait timed out in thread 002f, blocked by 0009, retrying (60 sec)
   0030:err:ntdll:RtlpWaitForCriticalSection section 0x7bce56c0 "loader.c: loader_section" wait timed out in thread 0030, blocked by 0009, retrying (60 sec)
   0031:err:ntdll:RtlpWaitForCriticalSection section 0x7bce56c0 "loader.c: loader_section" wait timed out in thread 0031, blocked by 0009, retrying (60 sec)
   ```

   不管它了 升级去。

9. 卸载之前安装的`wine`执行`sudo apt-get remove wine-stable`

   ![image-20200430095057374.png](https://upload-images.jianshu.io/upload_images/4652214-1b1719e6fa2c9553.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   完成卸载

10. 官方安装教程

    ## 安装 WineHQ 安装包

    ![Dialog-warning.svg](https://upload-images.jianshu.io/upload_images/4652214-95cfea6d708b00ed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)**WineHQ 仓库密钥在 2018-12-19 更改过。** 如果您在哪之前下载并添加过密钥，您需要重新下载和添加新的密钥，并运行 sudo apt update 将更改应用到软件仓库。

    ![Dialog-warning.svg](https://upload-images.jianshu.io/upload_images/4652214-59d73627598a2f83.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)**Ubuntu 18.04/Linux Mint 19.x 没有提供 FAudio，但最新版的 Wine 依赖该软件包。请参照 https://forum.winehq.org/viewtopic.php?f=8&t=32192 从 OBS 安装 FAudio。**（Ubuntu 19.10 及更新版本的 Ubuntu 的软件仓库已经包含了 FAudio 安装包。）

    如果您之前安装过来自其他仓库的 Wine 安装包，请在尝试安装 WineHQ 安装包之前删除它及依赖它的所有安装包（如：wine-mono、wine-gecko、winetricks），否则可能导致依赖冲突。

    如果您使用的是 64 位系统，请开启 32 bit 架构支持（如果您之前没有开启的话）：

    ```
    sudo dpkg --add-architecture i386 
    ```

    下载添加仓库密钥：

    ```
    wget -O - https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add -
    ```

    并添加仓库：

    |      For this version:      |                      Use this command:                       |
    | :-------------------------: | :----------------------------------------------------------: |
    |        Ubuntu 20.04         | sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ focal main' |
    |        Ubuntu 19.10         | sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ eoan main' |
    | Ubuntu 18.04Linux Mint 19.x | sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main' |
    | Ubuntu 16.04Linux Mint 18.x | sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ xenial main' |

    更新安装包：

    ```
    sudo apt update
    ```

    然后安装 **以下任一一个安装包**：

    |   稳定分支   | `sudo apt install --install-recommends winehq-stable `  |
    | :----------: | ------------------------------------------------------- |
    |   开发分支   | `sudo apt install --install-recommends winehq-devel `   |
    | Staging 分支 | `sudo apt install --install-recommends winehq-staging ` |

    如果 apt-get 提示缺少依赖，请先安装缺少的依赖，然后重复以上两步（update 和 install）。更多故障处理技巧请参考 [the FAQ entry on dependency errors](https://wiki.winehq.org/FAQ#How_do_I_solve_dependency_errors_when_trying_to_install_Wine.3F)。

    ------

    #### 如果您之前使用过来自发行版自己打包的安装包，您会发现它们和 WineHQ 提供的有以下不同：

    - 文件被安装在 /opt/wine-devel 或 /opt/wine-staging。

    - 没有为 Wine 的内置程序（winecfg 等等）创建菜单项，并且如果您是从发行版自己打包的安装包升级上来的，原来的菜单项也会被删除。您可以使用菜单编辑器自己再次创建。

    - 没有添加 Binfmt_misc 注册项。如果您想手动添加，请查看您使用的发行版关于 [update-binfmts](http://manpages.ubuntu.com/manpages/jaunty/man8/update-binfmts.8.html) 的文档。

    - WineHQ 当前没有提供 wine-gecko 和 wine-moon 的安装包。所以当创建新的 wine 配置目录时，您将会被询问是否下载这些组建。为了得到更好的兼容性，我们建议您选择“安装”。如果下载过程发生出错，请查看 [Gecko](http://wiki.winehq.org/Gecko) 和 [Mono](http://wiki.winehq.org/Mono) 的 wiki 页面来进行手动安装。

    - 从 Wine 5.7 开始，WineHQ 的 Ubuntu 安装包有一个 debconf 选项用于开启 CAP_NET_RAW 以兼容需要发送和接收 raw IP 包的应用程序。由于具有潜在的安全风险，并且大多数应用程序不需要该功能，该功能默认被关闭。需要该功能运行应用程序的用户可以在安装 Wine 之后运行

    ```
    dpkg-reconfigure wine-<branch>-amd64 wine-<branch> wine-<branch>-i386
    ```

    并且对接着的三个问题回答 yes 来开启 CAP_NET_RAW。（<branch> 请对应上文使用 devel，staging 或 stable 替换。）

    ------

    ## 无网络环境下安装

    为了给没有网络环境的 Ubuntu 机器安装 Wine，您需要另外一个带有网络连接的 Ubuntu 机器（或虚拟机）来下载 Wine 的 .deb 安装包和其相关依赖。

    其过程大致如下： 在有网络连接的机器上如上文所述：添加 WineHQ 源仓库并运行 apt update。

    接着清理无关的缓存，只留下安装 Wine 所需的：

    ```
    sudo apt-get clean
    sudo apt-get --download-only install winehq-devel
    sudo apt-get --download-only dist-upgrade
    ```

    复制 /var/cache/apt/archives 下所有的 .deb 文件到一个优盘：

    ```
    cp -R /var/cache/apt/archives/ /media/usb-drive/deb-pkgs/
    ```

    最后到无网络环境的机器上从优盘上安装所有安装包：

    ```
    cd /media/usb-drive/deb-pkgs
    sudo dpkg -i *.deb
    ```

    您可以使用类似的步骤来从官方安装 `winehq-staging` 安装包。

    ## 编译 WoW64

    Ubuntu 的 [Multiarch](https://wiki.winehq.org/Multiarch) 支持目前尚不完整，所以目前您无法简单地同时安装 32 位和 64 位库。如果您使用的不是 64 位系统，您将会需要创建一个独立的环境来安装和构建 32 位依赖。请查看 [Building Biarch Wine On Ubuntu](https://wiki.winehq.org/Building_Biarch_Wine_On_Ubuntu) 以获取更多关于在 Ubuntu 使用 LXC 的介绍，通用的构建信息请查看 [Building Wine](https://wiki.winehq.org/Building_Wine)。

    **<font color=red>总结起来就是:</font>**

    ```
    sudo dpkg --add-architecture i386 
    wget -O - https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add -
    sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main'
    sudo apt update
    sudo apt install --install-recommends winehq-stable
    ```


​    执行最后一步安装`sudo apt install --install-recommends winehq-stable`出问题了

​	 ![image-20200430095057374.png](https://upload-images.jianshu.io/upload_images/4652214-0c098f0e52f20b7e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

解决问题的思路就是：缺啥装啥

1. 安装`winehq-stable` 执行`winehq-stable`

   ![image-20200430095345988.png](https://upload-images.jianshu.io/upload_images/4652214-1be1b2b9d3663ccc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   继续整：执行`sudo apt-get install wine-stable-i386`

   ​	![image-20200430095530273.png](https://upload-images.jianshu.io/upload_images/4652214-fb12a02279808332.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   又有新的缺失：执行 `sudo apt-get install libfaudio0:i386`  

   ​	![image-20200430095718042.png](https://upload-images.jianshu.io/upload_images/4652214-d2c31bd1cfd974a2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   what???  由于ubuntu的源无法下载这个包,so 

   ```
   libfaudio0:i386
   https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/i386/libfaudio0_19.07-0~bionic_i386.deb
   
   libfaudio0:amd64
   https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/amd64/libfaudio0_19.07-0~bionic_amd64.deb 
   ```

   我的是amd64,下载好后执行 `sudo dpkg -i libfaudio0_19.07-0_bionic_amd64.deb`

   ​	![image.png](https://upload-images.jianshu.io/upload_images/4652214-575a15ffc2cf600c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   惊不惊喜 意不意外，继续`sudo apt-get install libsdl2-2.0-0` 好了,再次执行`sudo dpkg -i libfaudio0_19.07-0_bionic_amd64.deb` ok了。

   再来安装  `sudo apt-get install libsdl2-2.0-0:i386`

   ![image.png](https://upload-images.jianshu.io/upload_images/4652214-6647b1e0b02efcab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   输入`y`然后就安装好了。

   接下来：再试试`sudo apt-get install wine-stable-amd64`哈哈哈能执行了 ，但是这个网速好像不是很正经(盘他),在浏览器中打开`https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/main/`是这样的

   ​	![image.png](https://upload-images.jianshu.io/upload_images/4652214-306f99de465a3369.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   根据自己平台选版本。我的是`binary-amd64`点它。然后看看控制台：

   ​	![image.png](https://upload-images.jianshu.io/upload_images/4652214-86d608659397191f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   

   不用慌：

   ​	![image.png](https://upload-images.jianshu.io/upload_images/4652214-c5b1c50a89968b16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   

对比了下因该是这个了，那就用你的各种拉风的下载工具去下载吧。如果你的系统和我的一样那就省事了因为我会给你提供好。把下载好的文件放到你知道的路径下执行 `sudo dpkg -i wine-stable-amd64_5.0.0~bionic_amd64.deb ` 好了。

满心欢心的执行 `wine --version`然后

​	![image.png](https://upload-images.jianshu.io/upload_images/4652214-b2633ebf62a68b35.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

what？？？哪里出了问题，掐之一算有问题，回到第10步执行 稳定分支  `sudo apt install --install-recommends winehq-stable `

​	![image.png](https://upload-images.jianshu.io/upload_images/4652214-2a6779aad755cbbc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

接下来这么弄：

```bash
为所需的libfaudio0库添加PPA：
仅适用于Ubuntu 18.04，Linux Mint 19.x和Ubuntu 19.04，因为更高版本的Ubuntu在主存储库中已经具有libfaudio0。

sudo add-apt-repository ppa:cybermax-dexter/sdl2-backport
```

​	![image.png](https://upload-images.jianshu.io/upload_images/4652214-c030bf3c009d192c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

设给你下的就是等待了。。。

在来执行`wine --version`

​	![image-20200430123657260.png](https://upload-images.jianshu.io/upload_images/4652214-0f9d72c292528735.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

可以了至此`wine`安装好了。

7. 先配置`wine`,命令行输入`winecfg`,因为我的是`2k`的屏幕所以非常小，所以先来设置显示。(如果你的不是2k/4k屏幕可以不用设置)

 
![](https://upload-images.jianshu.io/upload_images/4652214-c92c25aceef90095.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   7.1 显示设置将`允许窗口管理器装饰窗口`取消(作用是去掉应用上面那条标题栏)，将屏幕分辨率设置为180`dpi`,这样看起来就舒服多了。
![image-20200429221958698.png](https://upload-images.jianshu.io/upload_images/4652214-9c5bf2dd7068759b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
	
   顺便说下虚拟桌面，选择虚拟桌面启动应用就会先启动一个窗口给你，安装的应用都在那个窗口里。好了到此基本都配置好了。

   7.2 执行`winetricks riched20`,这个是用来解决安装的应用输入框输入文字不显示的问题。

   ![解决应用输入框问题](https://upload-images.jianshu.io/upload_images/4652214-1be947a00a81e71a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   因为我已经把需要的下载好了所以直接就安装了，有个100MB 多的`exe`不好下载，后面我会打包好提供出来将我提供的应用包放到下面这个位置，然后再次执行`winetricks riched20`即可

   `/home/你的账户名/.cache/winetricks/win2ksp4/`

###　二、安装企业微信

1. 下载好企业微信(我的路径: `/home/chenyz/下载/wine/WXWork_3.0.16.1614.exe`)

2. 进入到目录`cd /home/chenyz/下载/wine/`

3. 执行`wine WXWork_3.0.16.1614.exe`，首次运行会出现`4、5`步骤

   ![启动安装企业微信程序](https://upload-images.jianshu.io/upload_images/4652214-b8922c26ecd9236d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. 取消安装`wine mono`,因为装不动不装影响不大(后面有影响在装)

   ![取消安装](https://upload-images.jianshu.io/upload_images/4652214-bea7d4f1c3892519.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5. 继续取消`wine Gecko安装器`（如果再弹继续取消）

   ![取消3](https://upload-images.jianshu.io/upload_images/4652214-ec94bd8ee0bcdb4c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6. 看到企业微信的安装界面了，点击`立即安装`(可能安装过程有些慢，耐心等待)

	![企业微信安装界面](https://upload-images.jianshu.io/upload_images/4652214-19d5915b3f55a907.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


7. 安装完成界面，点击立即使用

	![安装完成](https://upload-images.jianshu.io/upload_images/4652214-1cacfa34c2616b9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


8. 手机扫码就能登录了

	![安装完成](https://upload-images.jianshu.io/upload_images/4652214-8884771e8376b9b5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


9. 登录后效果

	![使用界面](https://upload-images.jianshu.io/upload_images/4652214-83c960276f6d4505.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   

尽情使用吧!!!

## 问题总结

- 首次使用或切换其他应用然后切换回来输入中文会变成方块，随便输入内容回车后再次数据就正常了
- 还有前面说到的截图不可用，使用`flameshot`代替(更好用)
  - 安装：`sudo apt-get install flameshot`
  - 设置>设备>键盘，设置一个自定义快捷键（拉到最下面）命令填写：`flameshot gui`
  - 快捷键设为`alt+a`
- 关于安装好后菜单栏有2个快捷方式的问题
  - 执行 `rm -rf /home/你的账户名/.local/share/application/wine/企业微信.desktop ` 删除即可

**使用到的资源(GitHub单文件超过100MB不让传):**
链接: https://pan.baidu.com/s/16CNlsXd6Py3_MOV7_cGc-A 提取码: pvm3 
	
	
**<font color=red>真实辛苦百度了网速限制的这么稳定</font> 再放个阿里云盘：**
	「w2ksp4_en.exe」，点击链接保存，或者复制本段内容，打开「阿里云盘」APP ，无需下载极速在线查看，视频原画倍速播放。
链接：https://www.aliyundrive.com/s/gx8zKvkbSiP

> 基本上完美了，O(∩_∩)O哈哈哈~ 如果使用过程中有什么问题可以给我留言或者发邮件 mailto:1290084841@qq.com 

**生命不息，折腾不止!**


<small>如果对你有帮助，那就赞赏作者吧！！！</small>
	
![支付宝.png](https://upload-images.jianshu.io/upload_images/4652214-49a02afb4086e0ab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![微信.png](https://upload-images.jianshu.io/upload_images/4652214-97f510652bacaf5d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



