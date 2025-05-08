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
## 变量
### 系统预定义变量
1. 常用系统变量
   $HOME,$PWD,$SHELL,$USER等。
   ![image](https://github.com/user-attachments/assets/50d6ebc8-33fa-41a3-98b9-dd7b4162b312)
3. shell中变量分类
   - 第一种
     - 系统定义好的变量
     - 用户自定义变量
   - 第二种
     - 全局环境变量（对子shell也有效）
     - 局部环境变量（只对当前shell有效）
3. 显示当前Shell中变量
   ```
   env
   echo $
   printenv（跟env一样）
   printenv USER（可以不加$符）
   set（看当前定义的所有变量）
   ```
### 自定义变量
1. 基本语法
   ![image](https://github.com/user-attachments/assets/bddc6457-05a7-4bfe-97e7-dab3194ffd9c)
   不关心变量类型，只需要赋值就行；而且等号左右不能加空格。
3. 例
   ![image](https://github.com/user-attachments/assets/d0cc0dff-bbaf-4050-8554-5b7e1aff9840)
   ![image](https://github.com/user-attachments/assets/effa8444-f5ec-4ab4-a622-6b1b4fb7c4d3)
   ![image](https://github.com/user-attachments/assets/79a2e7ed-79d0-4370-b8e5-b19ae89628a7)
   切换子shell后没有说明这样定义的my_var是局部变量。
   ![image](https://github.com/user-attachments/assets/d247a575-afc1-481c-8dc1-cf4292ea37c9)
   ``export xx``提升为全局变量
   ![image](https://github.com/user-attachments/assets/394f3a13-a642-4e2b-8548-7b5d761905fe)
   当前的全局变量可以在所有子shell中可以看到，但对该变量的更改只在当前shell中有效，子shell中更改无效。（儿子可以看爹的，但不能占为己有）
   ![image](https://github.com/user-attachments/assets/2abfbe1e-876f-461b-ace5-1b31036256d1)
   注意创建变量前要先检查系统里存不存在该变量。因为此时是个局部变量所以用相对路径没有输出，用``./source``才有输出。如果要让相对路径有输出需要将这个局部变量提升为全局变量。
   ![image](https://github.com/user-attachments/assets/c5a064ee-bdf9-4f61-b745-ebe605c6bc57)
3. 自定义一般是小写，大写一般是系统变量。
4. 默认定义是字符串，如果要用数值运算定义，需要用shell特定运算符。
   ![image](https://github.com/user-attachments/assets/327fe497-0c9e-4648-8f71-0365d0c8dee6)

6. 还可以定义只读变量（相当于静态变量/常量）
   ![image](https://github.com/user-attachments/assets/cf7a8406-9c1e-443b-8822-59f88c531b6b)
7. 撤销变量
   ![image](https://github.com/user-attachments/assets/4f8b94fe-36d5-4cd0-9115-83f50dabaf8d)
8. 变量定义规则
   ![image](https://github.com/user-attachments/assets/081aee55-bb8f-422f-b71b-2419fcf0d405)
9. 把hello.sh放到/bin目录下就可以直接用名字执行（当成命令一样执行），因为bin目录下存放的都是系统自带的命令。
### 特殊变量
1. $n
   - 基本语法
     ![image](https://github.com/user-attachments/assets/c22ab00a-dec9-47b4-b482-4ffadd9e38bc)
     ""能够识别字符串中的变量，而''不会，它会输出纯字符串
     ![image](https://github.com/user-attachments/assets/63b9c061-370b-4eb1-9c0b-5cdce39f1c16)
     ![image](https://github.com/user-attachments/assets/805ac8b8-04f1-4197-96a8-c2382ceca275)
2. $#
   - 基本语法
     ![image](https://github.com/user-attachments/assets/4e568fa4-2dd7-4d78-b889-4e8ef4acf3f1)
   - 例
     ![image](https://github.com/user-attachments/assets/cb85eb8a-4024-4ad1-b7eb-114d9f477bf5)

     ![image](https://github.com/user-attachments/assets/12018b87-bfd6-4fdd-bd59-69401b78af9d)
 3. $*,$@
    - 基本语法
      ![image](https://github.com/user-attachments/assets/2d171f07-e73d-453f-9fd7-4515a0db8054)
    - 例
      ![image](https://github.com/user-attachments/assets/a2e6ce1a-35a6-40ae-9b1b-b7c9934e22a3)
      不做循环看不出什么区别。
    - 两者不用""引起来的话没有任何区别
         ![image](https://github.com/user-attachments/assets/c1f9baec-c062-4cd1-8aae-d6110a0e0d95)
4. $?
   - 基本语法
     ![image](https://github.com/user-attachments/assets/b1e91e45-1fcb-4d3a-9ee2-d9d10cab3d76)
   - 例
     ![image](https://github.com/user-attachments/assets/d947ebe1-f012-42b2-a249-27ebfc5e9dbe)
## 运算符
- 基本语法
  $(()) | $[]
- 计算用expr（但是*要用\*）
- 例
  ![image](https://github.com/user-attachments/assets/0de9713d-1076-464e-9548-42f5a80e383e)
  ![image](https://github.com/user-attachments/assets/de1261bf-8506-4e65-9202-a8f78233b586)
  ![image](https://github.com/user-attachments/assets/2763a63a-19f4-4910-9765-363600e868f6)
  （2+3）*4的两种方式（第二种更好）
## 条件判断
- 基本语法
  ![image](https://github.com/user-attachments/assets/eba2e976-1aab-4d34-9b2a-49e38aeddf1b)
  中间的判断也需要空格
  - 例
    ![image](https://github.com/user-attachments/assets/7027fbba-029e-4b90-a3cc-b6deecc0eeda)
    ![image](https://github.com/user-attachments/assets/5d084bb6-8b5c-4ea7-b000-8d03d27823d3)
    ![image](https://github.com/user-attachments/assets/feeee990-9f28-4a7c-a110-2f7aaa50264c)
- 常用判断条件
  1. 整数间比较
     ![image](https://github.com/user-attachments/assets/9a08c8a7-8cb8-420b-84f5-cf993fe3ba65)
     - 例
       ![image](https://github.com/user-attachments/assets/c093d6d4-730d-4f10-a8d7-4df9e95af95e)
       此时是把它当字符串所做的比较
       ![image](https://github.com/user-attachments/assets/6e2c7eef-c634-4a87-bef2-1a0889020328)

  2. 判断文件权限
     ![image](https://github.com/user-attachments/assets/39d0ccb2-dc97-4ba3-a972-c870591cf39d)
     - 例
       ![image](https://github.com/user-attachments/assets/c2839c0a-785e-41b4-a549-5f774025e20f)

  4. 判断文件类型
     ![image](https://github.com/user-attachments/assets/0f51805a-7ec8-41ba-8d85-657346cb80e6)
  5. 多条件判断（跟平常用法一样）
     - &&表示前一条成功才执行下一条
     - ||表示上一条失败才执行下一条
     - 例
       ![image](https://github.com/user-attachments/assets/47fe73a6-da6e-4d99-bb8f-ea61046aefc5)
      类似if else/三元运算符
## 流程控制
1. if判断
   - 基本语法
     1. 单分支
        ![image](https://github.com/user-attachments/assets/e8188fc6-c370-4f5a-a10d-4d9c48c01a46)
        ![image](https://github.com/user-attachments/assets/b3020d5a-e861-4318-ad1a-f527ef8aa9e9)

     3. 多分支
        ![image](https://github.com/user-attachments/assets/6a666244-4963-43be-a9d5-77b346d8e62f)

     3. 例
        ![image](https://github.com/user-attachments/assets/c4e4daa5-3208-4e70-9ef2-563942f3a5aa)
        在一个中括号里&是-a，|是-o
        ![image](https://github.com/user-attachments/assets/07a4aba5-6dc3-4d3b-919f-0c2ab4d3e097)
        ![image](https://github.com/user-attachments/assets/f50e0df0-c443-43b8-b826-04dea91d33c9)
        ![image](https://github.com/user-attachments/assets/022c79b7-d89c-4d2a-829b-4af4946d83dd)

        ![image](https://github.com/user-attachments/assets/e072a647-4278-47a8-8b09-db60af55b71c)
2. case语句
   - 基本语法
     ![image](https://github.com/user-attachments/assets/f406488a-e650-4c2e-9e7a-579820d0c051)
   ``;;``相当于``break;``，``*)``相当于``default:``。
   - 例
     ![image](https://github.com/user-attachments/assets/3f7f7eb3-69ad-4587-9959-6850c72a1276)

     ![image](https://github.com/user-attachments/assets/2c30553e-06f0-4734-8bfd-78da308a2c8d)
3. for循环
   - 基本语法
     1. ![image](https://github.com/user-attachments/assets/d32d5bf3-2172-4781-aeb2-c8a7fb84f8ff)
        - 例
          ![image](https://github.com/user-attachments/assets/440d650f-1049-4baa-b310-7db9e2dfb383)
          双（）里可以直接用数学运算符号（<=）
          ![image](https://github.com/user-attachments/assets/9553e72d-7efd-4193-b60e-1d9335a8e212)
     2. ![image](https://github.com/user-attachments/assets/8ecc6cfa-ae0a-4e6a-9cb0-29818e4641a0)
        - 例
          ![image](https://github.com/user-attachments/assets/6cf63062-d548-43c1-adf9-d49f7128ba27)
4. while循环
   - 基本语法
     1. ![image](https://github.com/user-attachments/assets/cf79d2a6-7b88-4d4a-a902-5d8890712022)
        - 例
          ![image](https://github.com/user-attachments/assets/db2d4d3f-74b5-40e9-9e97-942ad41d2562)
          ![image](https://github.com/user-attachments/assets/271a32e6-2903-412a-9c02-76f840f204f1)
          新式写法是let加上在其他语言惯用的写法：
          ![image](https://github.com/user-attachments/assets/3958fbbd-c538-4ade-8d29-f7fb90ab6f6d)
## read读取控制台输入
- 基本语法
  （输出是echo重定向）
  ![image](https://github.com/user-attachments/assets/96500b81-c370-4132-a017-dc7443e2d19f)
  - 例
    ![image](https://github.com/user-attachments/assets/4c6e81ab-e13c-4de7-82fb-480613fdba02)
    ![image](https://github.com/user-attachments/assets/51370006-960d-4434-ac50-2c3a87bc0722)
## 函数
1. 系统函数
   1. basename
     - 基本语法
       ![image](https://github.com/user-attachments/assets/328db253-62ec-48e5-9799-8b0707e6cc0c)
       - 例
         ![image](https://github.com/user-attachments/assets/f9440f54-fa88-411a-90b2-ed70d2fec194)
         其实只是做了一个剪切的工作
         ![image](https://github.com/user-attachments/assets/df9a22e8-a56a-4ab3-8edd-3fbd69904501)
  
         ![image](https://github.com/user-attachments/assets/5f1f4cbb-1f23-4fab-8d7f-271576e5f625)
   2. dirname
     - 基本语法
       ![image](https://github.com/user-attachments/assets/2317de36-1fd5-4c01-ae9e-94309f5033a0)
       - 例
         ![image](https://github.com/user-attachments/assets/d2539fe3-5f0b-4d3f-a5e7-baac5a87b262)
         也只是做了剪切
         ![image](https://github.com/user-attachments/assets/f68da8ce-f6a3-454d-baaf-4a7584340ed9)
         ![image](https://github.com/user-attachments/assets/dc2a8f5e-ab2c-4d24-9927-586d321e1967)
         注意不能直接``dirname $0``，因为有可能输入的是相对路径，所以要用``pwd``获取绝对路径。使用``$()``调用系统函数的命令，shell中把这叫做***命令替换***，实际上就是系统函数的调用。
2. 自定义函数
  - 基本语法
    ![image](https://github.com/user-attachments/assets/05eedc59-3649-4c12-a5ae-762c8a6c0b33)
    []括起来表示可以省略。
  - 注意
    ![image](https://github.com/user-attachments/assets/6c61e000-66b0-4bea-80f1-96f3f4839a30)
    调用之前先声明；返回值在0-255。
## 总和应用
1. 归档文件
   ![image](https://github.com/user-attachments/assets/94f7cf8b-cfec-4290-b8c2-8b88e98ceff3)
   ![image](https://github.com/user-attachments/assets/f728e981-808d-42e5-b89c-cb99b05e3766)
   ![image](https://github.com/user-attachments/assets/34cd7fc0-d15f-46e2-93fd-675dd886b531)





     
   







     








   








