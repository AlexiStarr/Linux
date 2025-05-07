# 软件包管理
## RPM
redhat软件包管理工具（redhat package manager）
### 相关命令
1. 查询命令
   ```
   rpm -qa（查看系统所有软件包）
   rpm -qi 软件名（查看软件信息）
   ```
   由于软件包比较多，一般会用grep过滤。
2. 卸载命令
   ```
   rpm -e rpm软件包
   rpm -e --nodeps 软件包
   ```
   - 选项说明
     ![image](https://github.com/user-attachments/assets/3ef4e255-f837-455f-b9fd-2ad33ef50984)
3. 安装命令
   ```
   rpm -ivh rpm包全名
   ```
   - 选项说明
     ![image](https://github.com/user-attachments/assets/3ed253f2-4b07-42be-ab3e-5c65571761f9)
## YUM
是一个shell前端软件包管理器（yellow dog updater）。基于RPM，从指定服务器自动下载RPM包并安装，可以自动处理依赖关系，不用像RPM一样需要自己手动去下各种依赖。
- 相当于一个命令行的应用商店。
### 相关命令
```
yum [选项] [参数]
```
- 选项说明
  ![image](https://github.com/user-attachments/assets/ef58d7a1-fda9-4ca9-9756-933fd90601a3)
- 参数说明
  ![image](https://github.com/user-attachments/assets/b345d75a-518b-4ca3-ba18-1c183ab316a8)
# 克隆虚拟机
- 要改ip地址，不能完全一样，到  
  ``/etc/sysconfig/network-scripts/ifcfg-ens33``  
  里面改。  
- 然后重启networkmanager，查看是否修改成功。
- 改主机名  
  ``hostnamectl set-hostname xxx``  
  然后通过``hostname``查看
