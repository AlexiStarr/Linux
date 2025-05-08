# 概述
Shell是一个命令行解释器。将用户操作和linux内核连接起来，相当于翻译官。（包在内核外面的一个壳）
- 脚本文件：一行一行解释编程
- Shell作为编程语言，易编写、易调试、灵活性强。
# Shell脚本入门
- 脚本格式  
  以#!/bin/bash开头（指定解析器）
- 脚本运行
  ```
  1. bash xx.sh
  2. sh xx.sh
  3. chmod +x xx.sh（给该文件加可执行权限）
     绝对或者相对路径（./xx.sh也是相对路径）
  4. source xx.sh
  5. . xx.sh（与./xx.sh完全不同，前面的是直接打开子shell执行脚本，而这个是直接使用父shell）
  ```
  ![image](https://github.com/user-attachments/assets/a083a5d7-50ef-4a15-bcfe-710ff0a435a2)
  ![image](https://github.com/user-attachments/assets/7eef96b6-a7d0-4059-839a-79d3a75abe26)
