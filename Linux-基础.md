## 桌面和终端基本操作
- super键就是win键
- 打开控制台界面
  - centos7 ctrl+alt+f2
  - ubuntu ctrl+alt+f7
- 终端会话
  - root用户是#，普通用户是$
  - ~是主文件夹
  - 切换输入法win(super)+空格
  - linux中复制粘贴是ctl+shift+c/v
- 网络连接

  如果网络无法连接，并且ifconfig里面也没有ens33，可以检查接下来几个方面：  
  1. ``/etc/sysconfig/network-scripts/ifcfg-ens33``网络配置文件夹
  2. network.service和NetworkManager.service是否冲突。可以把后者关了，重启前者。
## 文件与目录结构
### linux文件
linux系统中一切皆文件
### 目录结构
![image](https://github.com/user-attachments/assets/f907e407-2ca7-478d-93e4-619380ea8235)
层级式目录结构（类树）
- 所有的硬件设备也皆以文件形式作管理
- 跟win相反，路径是/,win是\
- 挂载/挂载点
  - 在linux系统中要指定硬盘分区的文件系统格式（早期用ext4,centos7默认用xfs）
  - 挂载点：在根目录下但不一定在根分区中。如果要在不同分区放不同内容，需要在单独的区域设置挂载点。
  - 是一个逻辑上的结构关系，（在逻辑上在一起，但是物理上是映射分布）并不是真正意义上分区结构的存在方式，也叫做‘虚拟分区’。
### 目录的具体用法
![image](https://github.com/user-attachments/assets/c4a80e91-3d5d-415a-9236-076f056c0e98)
1. bin（binary）
   - 二进制目录，里面存放可以直接执行的常用命令。
   - 朝外的小箭头表示：此处的bin并不是直接存放在当前根目录下（类似快捷方式，只是一个链接）
     ![image](https://github.com/user-attachments/assets/10669fd7-ec02-450d-9163-35325a09e873)
2. sbin（system bin）
   - 系统级的二进制命令
3. lib（library）
   - 库目录，放系统和应用程序所需要的一些共享库文件，类似于win中的dll（动态链接库文件）
   - 此目录等同于win中的system32
4. lib64
   - 64位相关的一些比较特殊的库文件
   - 类win中的system
5. usr
   - 包含用户所有应用程序和所包含的数据
   - user system resource
6. boot
   - 用户数据千万不能写到这个文件夹
   - 引导启动的核心文件
   - 大小100-500mb足矣
7. dev（device）
   - 管理所有设备的目录
8. etc
   - 系统配置文件
9. home
   - 每个用户的主目录（用户个性化信息）
10. root
    - root用户的主目录
11. opt
    - 可选目录，给第三方软件包专门留下的位置
12. media
    - 识别可移动媒体设备的挂载点
13. mnt
    - 另外一个挂载点
14. proc
    - 进程目录，存放当前硬件和进程信息（别碰）
15. run
    - 运行目录，记录运行信息，重启就没了
16. srv
    - 跟系统服务相关（别动）
17. sys
    - 硬件相关信息（别动）
18. tmp
    - 临时目录
19. var
    - 日志，放可变的东西
- 系统相关目录最好不动
- opt、tmp、home、root、var、etc(谨慎）动了之后没事
## VI/VIM编辑器
### 是什么
- VI是unix中最通用的文本编辑器
- VIM是由VI发展来的更强大的文本编辑器，两者完全兼容
### VIM三种模式
![image](https://github.com/user-attachments/assets/a5fb57f2-abeb-4e4e-85a5-4672d1226ca0)
一般模式、编辑模式、命令模式

1. 一般模式
   - yy复制光标行
   - p粘贴（重复粘贴n次输入'n'p[仅3,4,5可以]）
   - 'n'yy复制好多行
   - dd删除当前行（可以ndd）
   - y$复制从当前光标位置开始到当前行结束的部分
   - y^复制光标前
   - yw复制词
   - d$
   - dw删除词
   - x删一个（往后删）
   - X往前删
   - r替换一个字符
   - R换多个字符，直到退出为止
   - w跳到下个词词头，e词尾，b上个词词头
   - gg文档开头，G结尾
   - u回滚
2. 插入模式
   - a i o（当前行下一行） 进入插入模式
   - 插入当前光标前
3. 命令模式
   - :w写入
   - :q退出
   - :wq写入退出
   - :q!强制退出
   - :set nu显示行号
   - :set nonu不显示
   - /查找词
   - :noh取消高亮
   - :s/被替换词/替换词 替换匹配到的第一个
   - :s/被替换词/替换词/g 当前行全替换
   - :%s/被替换词/替换词 换每一行第一个
   - :%s/被替换词/替换词/g 所有
## 网络配置和系统管理操作
### 查看网络IP和网关
- 通过ipconfig和ifconfig命令查看主机和虚拟机对应的ipv4地址，然后互相ping
- VMWARE提供的三种网络连接模式：
  - 桥接模式（最简单，配置的也最少）  
    主机起到网桥的作用，虚拟机可以直接访问外部网络，且对外部网络可见
    ![image](https://github.com/user-attachments/assets/7bb1ce9c-abd4-4956-bda2-774f0a688fb4)
  - NAT模式（学习生产中用得最多，安全私密性好）  
    network address transaction（网络地址转换）。通过共享主机IP访问外部网络，但外网无法访问虚拟机。
    ![image](https://github.com/user-attachments/assets/50d3deab-0f37-4f23-bacd-6495057eef42)
    构建了虚拟的局域网。给pc虚拟一个网卡，让它和虚拟网在一个子网，使主机和虚拟机可以互相访问。虚拟出的网卡叫vmnet8
  - 仅主机模式  
    虚拟机只与主机共享一个专有网络，与外部无法通信。
    ![image](https://github.com/user-attachments/assets/f20b778f-1099-45c5-8170-0c1f0b3a2c6f)
    虚拟出的网卡叫vmnet1
### 配置主机名
- 基本语法
  ```
  hostname
  ```
  ```
  hostnamectl set-hostname xxx
  ```
- 修改hosts映射文件  
  /etc/hosts
### 远程登录
- ssh命令
  ```
  ssh root@hadoop100
  ```
  exit退出
- 运用最多的远程登录工具是Xshell
## 系统管理
### linux中进程&服务
- 进程：一个正在执行的程序或命令
- 服务：启动后一直存在，常驻内存的进程
### service服务管理
- 基本语法（centos6）
  ```
  service 服务名 start|stop|restart|status
  ```
  所有的服务在/usr/init.d/服务名
- 守护进程  
  deamon，在linux中，系统服务和守护进程是一回事
- 基本语法（centos7）
  ```
  systemctl start|stop|restart|status 服务名
  ```
  所有服务在/usr/lib/systemd/system。.service就是服务，.target是服务的集合
### 修改开机自启动任务
通过setup图形化界面修改，通过tab切换最底下的选项，通过空格切换是否选中，最左边方框里的*代表已选中开机自启动。
### linux系统运行级别
- centos6  
有七种运行级别
![image](https://github.com/user-attachments/assets/2222cb49-f5d3-4c35-bffc-d640b18643fb)
0关机6重启35正常启动一个命令行一个图形界面1是安全模式可改root密码2不能上网的3,4是保留未定义
- centos7
  - 运行级别简化为
    - multi-user.target:3
    - graphical.target:5
    ![image](https://github.com/user-attachments/assets/c18f88d1-e732-465b-9fb1-d512300cb3eb)

  - 查看当前运行级别
    ```
    systemctl get-default
    ```
  - 修改当前运行级别
### 关闭防火墙操作
- 命令
  ```
  systemctl disable firewalld
  ```
  ```
  systemctl enable firewalld
  ```
  ```
  systemctl status firewalld
  ```
### 关机重启命令
- shutdown命令
  ```
  shutdown（默认一分钟之后关，因为要先sync同步内存中数据到硬盘）
  ```
  ```
  shutdown -c //撤销
  ```
  ```
  shutdown n/time （n分钟后/time时关机）
  ```
  ![image](https://github.com/user-attachments/assets/5726b7cf-c0e3-4ddc-b1d7-169b4fbd66ce)

- linux中的数据是预读延写
- halt命令，关闭系统但不断电
- poweroff关机断电
- reboot重启，等于shutdown -r now
