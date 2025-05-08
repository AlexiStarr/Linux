# 正则表达式入门
提取字符（串），做模糊式的匹配搜索。正则就是定义匹配规则。
## 常规匹配
   ![image](https://github.com/user-attachments/assets/16e7da57-e2b7-4098-b0b1-83f64c6241ad)
## 常用特殊字符（进行模糊匹配）
1. ^  
   匹配一行的开头
   ![image](https://github.com/user-attachments/assets/5a0e3ced-4a71-42ff-ab50-b489a5ced6e7)
   ![image](https://github.com/user-attachments/assets/c8cf8fa0-c8aa-42ff-b60e-769eeca6d6ed)

3. $  
   匹配一行的结束
   ![image](https://github.com/user-attachments/assets/f7f4c7c1-1d59-4ed4-9144-6f2cdc9d4027)
   ![image](https://github.com/user-attachments/assets/e2c29b22-766c-48a6-a29e-7962fc4bf2f0)
   显示空行及行号
5. .  
   匹配一个任意的字符
   ![image](https://github.com/user-attachments/assets/bf6ba41d-0fd8-470d-b2ba-729531034452)
5. *  
   不单独用，与上一字符连用，表示匹配上一个字符0次/多次
   ![image](https://github.com/user-attachments/assets/f1d538ce-15a1-4b85-8896-e05ad33f1664)
6. .*  
   表示任意字符串，包括空串，类似mysql中的%
   ![image](https://github.com/user-attachments/assets/bc032291-f864-485c-8cec-a39dafc48b98)
7. []  
   表示字符区间，例如：
   ![image](https://github.com/user-attachments/assets/0a3d37e3-14ff-4451-9740-a23377f13adb)
   ![image](https://github.com/user-attachments/assets/01a566a2-8841-476f-88ee-99f60752c495)
   （，可以去掉）
8. \  
   表转义，不会当度使用。由于所有特殊字符都有其固定匹配模式，因此当我们想要匹配某一字符本身时，就需要与转义字符连用，来表示其本身。
   ![image](https://github.com/user-attachments/assets/18d0674b-26ae-40eb-a248-7e99ace593c8)
   而且还必须要用单引号引起来。
   ![image](https://github.com/user-attachments/assets/87db32bb-f2c4-4f28-b87e-c09c2725d555)
## 实际运用-手机号码匹配
![image](https://github.com/user-attachments/assets/8b0798b3-4e6f-4cfa-a8e1-4a4fe820027a)
-E表示支持扩展写法``[0-9]{9}``出现九次
# 文本处理工具
1. cut
   在文本文件进行数据剪切
   - 基本用法
     ```
     cut [选项参数] filename
     ```
     默认分隔符是制表符
   - 选项说明
     ![image](https://github.com/user-attachments/assets/71c53bac-df45-45c2-824d-a09aaea55b05)
     -f列号-d分隔符-c切字符
   - 例
     ![image](https://github.com/user-attachments/assets/7fb35c50-683d-4eeb-a547-161078f372fb)
     ![image](https://github.com/user-attachments/assets/955a4eea-16ce-4989-b966-08ab0b9a55c6)
     ![image](https://github.com/user-attachments/assets/04cb4841-5ac8-479f-b72b-7a59143f4f9c)
     表示第三列及之后全部提取
     ![image](https://github.com/user-attachments/assets/a8c091b8-f471-4b65-b418-f85aaa532a30)
     前四列全部提取
     ![image](https://github.com/user-attachments/assets/b94e6459-d0f2-47b8-bafa-1d581f483d57)
     3-6列
     ![image](https://github.com/user-attachments/assets/57c8d6c4-6275-4bd4-bf7a-9623ae5f5bee)
     获取当前ip地址
     ![image](https://github.com/user-attachments/assets/2e408b42-437a-4a7f-a29c-3b8770f1c909)
     把所有ip地址都切出来
2. awk
   最强大的文本分析工具
   - 基本语法
     ![image](https://github.com/user-attachments/assets/19f614e8-8b68-474d-9bd9-7d58e7e9b1c1)
     pattern就是一个正则
   - 选项说明
     ![image](https://github.com/user-attachments/assets/cac2ea82-a5fc-402e-a19a-c9c556e4303b)
   - 例
     ![image](https://github.com/user-attachments/assets/a1c26fc5-4edc-4f88-8e8e-cb43a9ec6aed)
     ![image](https://github.com/user-attachments/assets/b5c959ce-c783-4cd1-b6ab-b62aaf4562e9)
     ![image](https://github.com/user-attachments/assets/5704d9a7-3a74-4028-81e2-5fbade5d7de5)
     ![image](https://github.com/user-attachments/assets/c9ffbad1-0fbd-4698-9a2f-24125c1225c4)
     用一对单引号就行了。
     将id号加一两种方法：
     ![image](https://github.com/user-attachments/assets/bf256999-9b94-4dd2-aa01-fa8c2d36bcdc)
     将id号加一
   - awk内置变量
     ![image](https://github.com/user-attachments/assets/255b6876-fbd4-4fa2-bc16-7b8832213aea)
   - 例
     ![image](https://github.com/user-attachments/assets/75649118-d265-4629-a72a-c407d4af9a8a)
     用awk的话前面的空格就不算列了，因此是第二列，用cut的话就算，是第十列。
     ![image](https://github.com/user-attachments/assets/3fa520a2-f037-4bd2-b2b2-b19a05314ce1)
## 综合运用
![image](https://github.com/user-attachments/assets/29426e49-6b7c-47e0-9eed-5ddd72fd9b62)



     




