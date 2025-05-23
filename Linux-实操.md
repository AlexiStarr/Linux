# 基本常用命令（重要）
- shell：可以看作一个命令解释器，提供交互式的文本控制台界面。我们可以通过终端输入命令，由shell进行解释并最终交给内核执行。
- bash（全程Bourne Again Shell）：linuxOS默认的，是Bourne Shell的扩展
## 帮助命令
部分基础功能的系统命令（例如cd）是直接内嵌在shell中的，系统加载启动后会随shell一起加载，常驻在系统内存中，这部分命令被称为内置（built-in）命令，其他命令则为外部命令。
- 判断命令类型
  ```
  type 命令
  ```
  ![image](https://github.com/user-attachments/assets/f2aad592-9925-43cf-aaa3-70dab43a73ed)
- man获得帮助信息（manual手册）
  - 基本语法
    ```
    man 命令名称
    ```
- help获取shell内置命令的帮助信息
- 命令 --help（适用于外部命令） 
## 常用快捷键
![image](https://github.com/user-attachments/assets/78f290f4-9ad5-4fe4-b8ed-57fc30a8fa96)
## 文件目录类
1. pwd（print working directory）
   - 基本语法
     ```
     pwd（显示当前工作目录的绝对路径）
     ```
     ![image](https://github.com/user-attachments/assets/ac9903bb-7117-44f6-bfd8-1117a6baf9bd)
     ![image](https://github.com/user-attachments/assets/d378a887-2e39-42a6-8c1e-b7abce450dff)
   - 绝对路径：从根目录开始到当前结点 的路径
   - pwd -P是实际的物理路径，在软链接出现时使用
     ![image](https://github.com/user-attachments/assets/5f2cadb4-2ef3-4917-b8f3-6d652054cd65)
    用pwd查询是此时软链接的查询路径，而加上-P则是实际指向的物理路径。
2. cd
   - 基本语法
     ```
     cd /root/桌面/
     cd /root/桌面
     cd 桌面
     cd ../视频
     cd .（当前目录）
     cd ./视频
     cd ..（上一级目录）
     cd ~（root目录）
     cd -（回到上次的目录）
     cd /（根目录）
     ```
    - 软链接-P
      ![image](https://github.com/user-attachments/assets/c309b1d6-0866-4c2a-9c89-cd5efc5988d4)

3. ls
   - 基本语法
     ```
     ls [选项] [目录/文件]
     ```
   - 选项
     ![image](https://github.com/user-attachments/assets/fd5da7fb-bc53-47fc-9d75-7441336638f7)
     - -a全部文件，连同隐藏的（开头为.的文件）
     - -l等价于ll
     - -lh显示出所有文件大小的单位
    - 例
      ![image](https://github.com/user-attachments/assets/7f37c0a2-076b-46cb-b072-ed4dd5e04e52)
4. mkdir  
   创建文件夹
   - 基本语法
     ```
     mkdir 文件夹名（当前路径下创建）
     mkdir /文件夹名（在根目录下）
     mkdir 文件夹名1 文件夹名2
     mkdir d d/e d/e/f（嵌套） = mkdir -p d/e/f（连不存在的父节点一起创建）
5. rmdir  
   删除文件夹，跟mkdir一样 ，但是只删除空文件夹    
6. touch  
   创建新文件
   - 基本语法
     ```
     touch 文件名
     ```
     以/为起点的算是绝对路径
7. cp  
   复制文件或目录
   - 基本语法
     ```
     cp [选项] source dest（复制source文件到dest）
     ```
   - 选项说明
     - -r递归复制整个文件夹  
   - 例
     ![image](https://github.com/user-attachments/assets/05315d4a-f9c9-446b-968c-5b02bfb932a6)
     此处加了\后不再出现是否覆盖询问，而是直接覆盖。事实上这个\的意思是直接使用linux的原生命令
8. rm  
   删除文件或目录
   - 基本语法
     ```
     rm [选项] deletefile（递归删除目录中所有内容）
     ```
   - 选项说明
     ![image](https://github.com/user-attachments/assets/b8c7f830-8b0d-40f8-8136-47215c559775)
   - rm默认删除文件，要删文件夹-r（但是要确认很多遍），此时可以用rm -rf就可以直接删干净文件夹
     ```
     rm -rf /*（是把系统上所有东西都删干净的意思）
     ```
     ![image](https://github.com/user-attachments/assets/1027a1f3-125b-47cd-b145-e18994a9babf)
     将当前目录所有文件都删掉，但保留目录
9. mv  
   移动文件与目录或重命名
   - 基本语法
     ```
     mv oldNameFile newNameFile（重命名）
     mv /temp/moveFile /targetFolder（移动文件，相当于剪切）
     ```
10. cat  
    查看文件内容，从第一行开始显示（catch）
    - 基本语法
      ```
      cat [选项] 文件名
      ```
    - 选项
      - -n会显示每一行的行号
    - 一般针对比较小的文件，一屏幕能显示全的
11. more  
    文件内容分屏查看器。是一个基于VI编辑器的文本过滤器。
    - 基本语法
      ```
      more 要查看的文件
      ```
    - 操作说明
      ![image](https://github.com/user-attachments/assets/7ec57c55-365c-4d7b-b2e6-46d5f3e672da)
12. less   
    分屏显示文件内容。功能类似more，但更强大，对于大型文件的效率很高
    - 操作说明
      ![image](https://github.com/user-attachments/assets/ecdc94b2-752b-4440-b435-e1d25c7878d8)
13. echo    
    输出内容到控制台
    - 基本语法
      ```
      echo [选项] [输出内容]
      ```
    - 选项
      - -e 支持反斜线控制的字符转换
      - 控制字符
        ![image](https://github.com/user-attachments/assets/bba58fe6-9e7a-4b10-a26a-8a9e55386d49)
        ![image](https://github.com/user-attachments/assets/e4ad90ce-be9b-457b-9018-aa99f93b3022)
    - 查看系统环境变量
      ```
      echo $
      ```
      ![image](https://github.com/user-attachments/assets/013db43c-110b-4ff8-a51e-cac0a2ebde1c)

14. > >>  
    >输出重定向，>>追加
    - 基本语法
      ```
      ls -l > 文件（将列表中内容覆盖写入文件中）
      ls -al >> 文件（将列表中内容追加至文件中）
      cat 文件1 > 文件2 （文件1内容覆盖到文件2）
      echo "内容" >> 文件
      ```
      ![image](https://github.com/user-attachments/assets/def21e08-7d3e-41f6-b1d3-b2fc138cf290)
      ![image](https://github.com/user-attachments/assets/25249781-e28a-4e6c-9e08-7ce8ed0eeb54)
15. head  
    显示文件头部内容，默认显示前十行。
    - 基本语法
      ```
      head 文件
      head -n x 文件（查看前x行）
      ```
16. tail
    输出尾部内容，默认后十行
    - 基本语法
      ```
      tail 文件
      tail -n x 文件
      tail -f 文件（follow的意思，实时追踪该文档的所有更新）
      ```
    - 对于tail -f  
      ctrl+s暂停，ctrl+q继续，ctrl+c退出，此时交互文件只能追加无法复写。此时如果用vim修改也无法检测到，因为vim修改相当于是临时创建了一个文件，在保存的时候再进行覆盖，在这个过程中索引号不同，因此无法检测到。
17. ln  
    创建软链接，软链接也叫符号链接，类似于快捷方式和C中的指针。
    - 基本语法
      ```
      ln -s [原文件/目录] [软链接名]
      ```
      如果直接``ln 文件 链接``得到的是硬链接。硬链接就是指针，软链接是指向指针的指针。
      - 不管软连接还是硬链接都是为了实现文件的共享而非复制
      - 可以理解为源文件在地址1，而系统供我们用的是指针a，软是指向a，而硬是直接指向地址1。
    - 技巧
      - 删除软链接
        ```
        rm -rf 软链接名
        ```
        注意：不能用/结尾如果用/结尾，会把软链接对应的真实目录下文件删掉
      - 查询
        通过ll就能查看，列表属性第一位是l，尾部会有位置指向。
18. history  
    查看已执行过的历史命令
    - 基本语法
      ```
      history
      history n（最近n条指令）
      !指令号
      history -c（清空）
      ```
      ![image](https://github.com/user-attachments/assets/17f49adc-e70c-4df6-b7bf-33daad41ff6f)
## 时间日期类
1. date
   显示当前时间
   - 基本语法
     ```
     date
     date +%Y（当前年份，2022，小写y只有22）
     date +%m
     date +%d
     date +"%Y-%m-%d %H:%M:%S"（年月日时分秒）
     date +%s（时间戳，从70年1月1日到当前）
     date -d "多久之前"
     date -s "字符串时间"（设置当前系统时间）
     ```
     ![image](https://github.com/user-attachments/assets/2f385124-7cd0-493c-bcdc-42fc5379fc1e)
     ![image](https://github.com/user-attachments/assets/bdffb1ed-a08e-41c1-beee-8fc6dbca3ef8)
2. cal  
   查看日历
   - 基本语法
     ```
     cal（查看本月日历，默认周日开头。eg:5月）
     cal -3（查看456月日历）
     cal 年份（查看全年日历）
     cal -m（星期一开头）
## 用户管理命令
1. useradd  
   添加新用户
   - 基本语法
     ```
     useradd 用户名
     useradd -d 路径名 用户名
     useradd -g 组名 用户名（添加新用户并加入某个组）
     ```
     ![image](https://github.com/user-attachments/assets/ad1715f6-f8bf-4097-b5c8-0041b85e6d08)
     设置密码用``passwd 用户名``，如果显示密码不合格，重复输两次即可。
   - 单个验证用户是否存在``id 用户名``
   - 查看所有用户``less /etc/passwd``
   - 切换用户``su 用户名``，用户的切换是层层嵌套，所以可以直接通过``exit``退出返回。
   - who命令，注意whoami的不同，直接用who也行
     ![image](https://github.com/user-attachments/assets/d691f8c0-5ef9-4312-ab0c-a92823e42f9f)
2. sudo  
   设置普通用户临时赋予root权限
   ![image](https://github.com/user-attachments/assets/ca051e7e-dd1e-43cb-9cd4-0b1c46aebe49)
   需要在sudoers中加入用户tony，路径是``/etc/sudoers``
   ![image](https://github.com/user-attachments/assets/21c15c1d-fe7c-413a-8f0f-fe64ffefbb3f)
   ![image](https://github.com/user-attachments/assets/1754e291-5b8f-47ff-a42f-6a9e7a208c79)
3. userdel  
   删除用户
   ![image](https://github.com/user-attachments/assets/1f8411c6-d4ab-496b-b894-91e62c9db177)
   虽然用户的系统文件夹还存在，但其实用户已经被删掉了。
   ![image](https://github.com/user-attachments/assets/78974e79-4560-4d29-af1f-08c4cbcd2811)
   加上-r可以把对应主目录也删掉
4. who
5. su
6. usermod
   修改用户
   - 基本语法
     ```
     usermod -g 用户组 用户名
     ```
## 用户组管理命令
1. groupadd  
   新建组
   - 把组加入sudoers要在组名前加%
3. groupmod  
   修改组
   - 基本语法
     ```
     groupmod -n 新组名 旧组名
     ```
4. groupdel  
   删除组
## 文件权限类
### 文件属性
1. 查看访问权限``ll``或``ls -l``
   - 如果-开头证明是文本文件，d开头是目录，l开头是链接，还有c字符类型设备文件、b块设备文件。
   - 一共是十位，除第一位每三位表示一种权限
     ![image](https://github.com/user-attachments/assets/31a02071-8a54-4095-8b47-48509e1439f7)
     如果没有权限就是减号-
     - 1-3是属主（该文件所有者）拥有该文件的权限 --user
     - 4-6是属组（所有者的同组用户）... --group
     - 7-9是其他用户... --other
2. rwx作用于文件和目录的不同解释
   - 文件
     ![image](https://github.com/user-attachments/assets/6fce33f6-8b68-48ee-9b12-339d028dab45)
   - 目录
     ![image](https://github.com/user-attachments/assets/f1bc9903-4808-4a63-859b-3fba839adba8)
3. ll命令所显示的参数是什么
   ![image](https://github.com/user-attachments/assets/f03cf82d-d0ec-49a1-82f7-54bde7022cef)
### 相关命令
1. chmod  
   改变权限（change mode）
   - 基本语法
     ```
     chmod [{ugoa}{+-=}{rwx}] 文件或目录 （a是所有都要改）
     chmod [(mode=)421] [文件或目录]（r=4,w=2,x=1;rwx=7）
     ```
     ![image](https://github.com/user-attachments/assets/4e5409c6-ce31-44eb-a324-283b135ad4cf)
   - 加``-R``可以递归修改目录下所有文件权限
2. chown  
   改变所有者
   - 基本语法
     ```
     chown [选项] [最终用户] [文件/目录]
     ```
   - 同样``-R``递归操作
3. chgrp  
   - 基本语法
     ```
     chgrp [最终用户组] [文件/目录]
## 搜索查找类
1. find  
   查找文件或目录
   - 基本语法
     ```
     find ([搜索范围]) [选项]
     ```
   - 选项说明
     ![image](https://github.com/user-attachments/assets/51c98789-9554-4ffe-b962-0658bf5b7ba7)
   - *的使用
     ![image](https://github.com/user-attachments/assets/e5ea4252-0dbc-4f14-a72f-782e862452f9)
   - 例
     ![image](https://github.com/user-attachments/assets/875f03d6-2e3a-4e6e-999c-bb4e939d3eae)
     ![image](https://github.com/user-attachments/assets/acc3a570-a6ce-4213-8721-4cf547ddeed8)
2. locate  
   利用事先建立的系统中所有文件名称及路径的locate数据库进行快速定位，查询速度特别快。但管理员必须定期更新locate数据库（默认每天自动更新一次）
   - 实操
     ```
     updatedb（运行前用其创建/更新locate数据库）
     locate tmp
     ```
3. which  
   定位命令
4. whereis  
   定位命令
6. grep  
   过滤查找及|管道符
   - 基本语法
     ```
     grep 选项 查找内容 源文件
     ```
   - 选项说明  
     -n 显示匹配行及行号
   - |管道符  
     相当于构建了一个管道，前面命令的操作结果通过管道传输给后面命令，作为后面命令的参数，继续处理。
     ![image](https://github.com/user-attachments/assets/5cea27c6-3e6d-4926-98be-c8f6af94a5b7)
   - wc  
     统计有多少行，多少个单词，多少字节大小
     ![image](https://github.com/user-attachments/assets/1aa4fcd4-2e32-45d8-9444-3663c7e2625c)
     ![image](https://github.com/user-attachments/assets/7fd01057-4a2a-4404-ad8b-0f2ecd49154a)
## 压缩解压类
1. gzip/gunzip
   - 基本语法
     ```
     gzip 文件（压缩文件，只能压成.gz）
     gunzip 文件.gz（解压文件）
     ```
   - 注意
     - 只能压缩文件不能压缩目录
     - 不保留源文件
     - 同时多个文件会产生多个压缩包
2. zip/unzip
   - 基本语法
     ```
     zip [选项] xxx.zip 要压缩的内容
     unzip [选项] xxx.zip
     ```
   - 选项说明
     ![image](https://github.com/user-attachments/assets/2eaaec1f-716e-4751-a415-406066d7cf90)
     ![image](https://github.com/user-attachments/assets/b73d809a-9d72-4c32-83eb-6b5b20af7856)
3. tar
   - 基本语法
     ```
     tar [选项] xxx.tar.gz 要打包进去的内容
     ```
   - 选项说明
     ![image](https://github.com/user-attachments/assets/f4fd4307-9c6c-4b66-b29c-8299458f562a)
     （它是打包起来后用gzip压缩，因此格式是gz）
     ![image](https://github.com/user-attachments/assets/008ca9e3-ef3e-45c3-8743-d73928611648)
     ![image](https://github.com/user-attachments/assets/275e6e78-7a26-4caf-99f3-15033536e12b)
     zcvf&zxvf
## 磁盘查看和分区类
1. du  
   查看文件和目录占用的磁盘空间（disk usage）
   - 基本语法
     ```
     du 目录/文件
     ```
   - 选项说明
     ![image](https://github.com/user-attachments/assets/fea6467e-8ed2-497e-829b-e56009b6f031)
2. df  
   查看磁盘使用情况（disk free）
   - 基本语法
     ```
     df 选项
     ```
   - 选项说明
     -h
   - 例
     ![image](https://github.com/user-attachments/assets/e5402127-c994-4b13-8779-beff92cbe644)
3. free  
   查看内存使用情况  
   选项：-h
4. lsblk  
   查看设备挂载情况（list block，列出块设备如硬盘、光盘的挂载情况）
   - 选项说明
     ![image](https://github.com/user-attachments/assets/169c71b5-b957-4889-b4f8-72309aa15a2a)
     ![image](https://github.com/user-attachments/assets/7869e8f0-8970-4081-9d2b-e20a0e7cfd73)
     /boot引导分区，[SWAP]交换分区（相当于虚拟内存），第三个挂载到根目录下。sr0是光驱（初始下载centos系统的光驱）
     ![image](https://github.com/user-attachments/assets/28dd8ffb-b0aa-453e-b29e-ccccfc1fe938)
     此时显示了文件系统类型
5. mount/umount  
   挂载/卸载
   ![image](https://github.com/user-attachments/assets/0fc69a93-d9ef-4ffc-996f-af7c85533148)
   - 基本语法
     ```
     mount [-t vfstype] [-o options] device dir（挂载设备）
     umount 设备文件名/挂载点（卸载设备）
     ```
   - 参数说明
     ![image](https://github.com/user-attachments/assets/4966927b-e26e-45d6-82e7-e8e32c8ed670)

   - 例
     ![image](https://github.com/user-attachments/assets/21fe8845-05f2-4fc0-abd6-4bc9ebc60a0f)
     查看光盘的挂载点并进入
6. fdisk  
   分区
   - 基本语法
     ```
     fdisk -l（查看磁盘分区详情）
     fdisk 硬盘设备名（对新增磁盘进行分区操作）
     ```
   - 选项说明  
     -l 显示所有磁盘的分区列表
   - 必须在root用户下才能使用
     ![image](https://github.com/user-attachments/assets/e3404884-dc14-4e64-968f-61493262a4f8)
     boot表示是否是当前的启动（/引导）分区。
     - ``mkfs -t 文件系统类型 设备名称``设置硬盘文件系统
## 进程管理类
1. ps  
   查看当前系统进程状态（process status）
   - 基本语法
     ```
     ps aux | grep xxx（查看系统中所有进程）
     ps -ef | grep xxx（查看子父进程之间的关系）
     ```
   - 选项说明
     ![image](https://github.com/user-attachments/assets/db766d3e-762c-458d-9b3a-15b4088f6e10)
   - ps aux 的参数说明
     ![image](https://github.com/user-attachments/assets/ffce394a-2731-461f-ae47-45bb94a529de)
     <表示当前进程优先级高，N表示低优先级；  
     0号进程是idle，一号是systemd，二号是kthreadd（管理线程）。
   - 如果想看CPU占用率和内存占用率，用aux
   - 如果想看父进程ID，用-ef
   - 真实终端是tty，模拟终端（例如在虚拟机中右键打开的终端）以及远程终端（ssh连接）都是pts。
2. kill
   终止进程
   - 基本语法
     ```
     kill [选项] 进程号（pid）
     killall 进程名称（也支持通配符）
     ```
   - 选项说明
     -9 强迫进程立刻停止
3. pstree  
   - 选项说明
     ![image](https://github.com/user-attachments/assets/0e451ad8-5955-4cc1-9493-20d15bd2cec1)
4. top  
   实时监控系统进程状态（实时版ps）
   - 选项说明
     ![image](https://github.com/user-attachments/assets/b433d199-9660-4ba1-ae41-6bc47825a281)
   - 操作说明
     ![image](https://github.com/user-attachments/assets/af36507a-1cae-417c-bde0-520bf02599b6)
5. netstat  
   查看网络状态
   - ifconfig、ping
   - 基本语法
     ```
     netstat -anp | grep 进程号（查看该进程网络信息）
     netstat -nlp | grep 端口号（查看网络端口号占用情况）
     ```
   - 选项说明
     ![image](https://github.com/user-attachments/assets/822beea9-5008-490a-ad01-db4dedd74c65)
6. crontab
   系统定时任务
   - 选项说明
     ![image](https://github.com/user-attachments/assets/20f2983f-4515-4750-b1d8-49daed7cf0a2)
   - 使用说明
     ![image](https://github.com/user-attachments/assets/ce819e3f-7487-4b63-8f00-25bcdca4d84e)
     分时天月几
     ![image](https://github.com/user-attachments/assets/b1a0474d-e57c-4f88-a974-b1c6c1556037)


