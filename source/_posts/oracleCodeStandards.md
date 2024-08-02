---
title: Oracle编码规范
date: 2024-08-02 01:05:52
tags: Oracle
index_img: /img/oracle.png
banner_img: /img/robot1.jpeg
---
> 编码规范的意义：代码美观，易于阅读理解/降低维护成本/降低出错概率/提升代码执行效率
>
> 感触：简单才是美

### :one:命名

**对象命名**= `对象前缀+模块名+对象标识` v_act_custinfo

| 对象类型               | 对象前缀 | 格式                |
| ---------------------- | -------- | ------------------- |
| 临时表 temporary table | t        |                     |
| 视图 view              | v        | v_表名              |
| 序列 sequence          | s        | s_表名              |
| 索引 index             | idx      | idx_表名_每列首字母 |
| 主键 primary key       | pk       | pk_表名             |
| 过程 procedure         | p        |                     |
| 函数function           | f        |                     |

**变量命名** = `变量前缀+变量标识`

| 变量类型     | 前缀 | 示例         |
| ------------ | ---- | ------------ |
| 局部变量     | v    | v_begin_date |
| 输入输出参数 | p    | p_oc_date    |

**常用英文简写**(原则上简写应不产生歧义)

| 全写         | 简写 |
| ------------ | ---- |
| information  | info |
| customer     | cust |
| description  | desc |
| destination  | dest |
| source       | src  |
| config       | cfg  |
| organization | org  |
| control      | ctrl |
| department   | dept |
| employee     | emp  |
| business     | biz  |

>通常不应使用**数字**/**特殊字符**来定义标识符
>
>避免使用数据库**关键字**&**保留字** 如: count
>
>长度<=**30**个字符

### :two:书写

**缩进**

1 缩进2空格，同一条语句中每个关键字单独成行，右对齐 

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle1.png)

**换行**

1 段语句单独成行

2 程序块之间用一个空行隔开

3 较长语句适当换行

4 在低优先级操作符处，操作符放在行首，并适当缩进

5 关键字独立成行：`DECLARE` `AS` `RETURN` `BEGIN` `END` `EXCEPTION`

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle2.png) 

**格式**

1 除字符串外，统一使用小写字符书写

2 操作符前后应以空格分隔，间隔符之后应以空格分隔

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle3.png)

3 insert语句中，select中的字段应与insert中的字段在位置上——对应

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle4.png)



### :three:注释

1 脚本文件、函数、过程头部应加注释

2 注释内容包括:创建者、创建日期、功能描述、修改记录等

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle5.png) 

3 注释应紧靠其描述的代码，在代码的上方或者右方

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle6.png) 

4 注释与所描述的代码进行同样的缩进

5 通过对函数、过程、变量等进行合理命名，使其成为自注释的



### :four:语法

1 使用SQL99语法标准，连接条件写在 `on` 里，过滤条件写在 `where` 里

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle7.png) 

2 不允许使用 `select *`，将需要的字段一一列出

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle8.png) 

3 insert语句中必须列出要插入的字段名

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle9.png) 

4 当sql中涉及多个表时，字段名应+前缀表名/表别名，别名不要重复

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle10.png) 

5 尽量使用静态sql，少用动态sql

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle11.png) 

6 使用通用语法和函数. 如用 `case` 代替 `decode` (Oracle特有函数，放到MySQL里就不会识别)

7 不使用 `goto` (跳跃性)语句来控制流程

8 少用游标(代码效率差)



### :five:优化

1 where中应避免隐式转换，避免对索引列使用丞数

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle12.png)

2 表的更新操作用 `merge` 代替 `update`

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle13.png) 

3 避免函数频繁执行

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle14.png) 

4 尽量避免使用 `or` 操作符

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle15.png) 

5 动态sql应使用绑定变量

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle16.png) 

6 判断存在性时，要加上 `rownum=1`

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle17.png) 

7 变量赋值尽量用 `:=`，比 `select into` 快

![](https://github.com/Kukukukiki192/TyporaImg/raw/main/img/oracle18.png) 