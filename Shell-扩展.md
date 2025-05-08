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
