---
title: Excel常用函数
author: BufferC
img: 'https://files.islu.cn/article/Excel.gif'
top: false
toc: true
mathjax: false
categories: Excel
tags:
  - Excel
  - Excel常用函数
keywords: 'Excel常用函数,Excel,函数,常用函数'
summary: Excel常用函数
abbrlink: 57189
date: 2021-03-15 14:23:21
---

# Excel函数

### 1、求和函数SUM()

> **SUM**函数将为值求和。 可以将单个值、单元格引用或是区域相加，或者将三者的组合相加。

1、指定数值求和

```excel
=SUM(10,20,30)
```

2、指定单元格求和：输入=sum()，在括号中间按住ctrl连续点击即可选择需要求和的数据

```excel
=SUM(C5,C9,C3)
```

3、也可以将指定单元格直接相加

```excel
=SUM(C2 + C4)
```

4、区域求和，输入=sum()，在括号中间按住ctrl选中所需要求和的数据

```excel
=SUM(C2:C11)
```

5、多个区域求和，输入=sum()，在括号中间分别按住ctrl选中所需要的多个区域的数据

```excel
=SUM(C2:C4,C6:C10)
```

6、配合固定值进行求和，中间使用英文的逗号分隔

```excel
=SUM(C2:C11,100)
```

### 2、条件求和函数SUMIF()

> 按条件求和

sumif函数的语法格式

> ```excel
> =sumif(range，criteria，sum_range)
> ```
>
> Sumif（条件区域，求和条件，实际求和区域），第二个求和条件参数在第一个条件区域里。

```excel
=SUMIF(D2:D11,D4,C2:C11)
```

求和所有性别中性别为女的年龄

### 3、求平均值函数AVERAGE()

> 获取平均值

1、指定数值求平均值

```excel
=AVERAGE(10,20)
```

2、指定单元格求平均值:括号内按ctrl选择需要求平均值的单元格

```excel
=AVERAGE(C2,C8)
```

3、范围单元格求平均值

```excel
=AVERAGE(C2:C11)
```

### 4、求最大值函数MAX()

> 获取最大值

1、指定数值求最大值

```excel
=MAX(30,40)
```

2、指定单元格求最大值

```excel
=MAX(C5,C11,C7)
```

3、指定范围单元格求最大值

```excel
=MAX(C2:C11)
```

4、指定多个范围单元格求最大值

```excel
=MAX(C3:C4,C7,C10)
```

### 5、求最小值函数MIN()

> 获取最小值

1、指定数值求最小值

```excel
=MIN(30,40)
```

2、指定单元格求最小值

```excel
=MIN(C5,C11,C7)
```

3、指定范围单元格求最小值

```excel
=MIN(C2:C11)
```

4、指定多个范围单元格求最小值

```excel
=MIN(C3:C4,C7,C10)
```

### 6、计数函数COUNT()

> 获取指定单元格非空数据数值类型的个数，对于空单元格、逻辑值或者文本数据将被忽略。可以用来判断是否有空白单元格

1、指定数值获取非空数值的个数

```excel
=COUNT(1,2)
```

2、获取指定单元格中非空数值的个数

```excel
=COUNT(C10,F10)
```

3、指定范围获取非空数值的个数

```excel
=COUNT(C10:C12)
```

4、指定多个范围单元格获取非空数值的个数

```excel
=COUNT(C8,C10,C12,F4:F12)
```

### 7、非空计数函数COUNTA()

> 统计区域内包含文本和逻辑值的单元格个数。
>
> 注意counta函数与count函数的区别。
>
> Count函数只统计区域内包含数字的单元格个数。

1、指定多个范围单元格获取非空数据的个数

```excel
=COUNTA(E4:E7,C2)
```

### 8、四舍五入函数ROUND()

> 对数值进行四舍五入

ROUND函数语法格式：

> ```excel
> ROUND(number, num_digits)
> ```
>
> 其中
>
> number表示需要进行四舍五入的数值或单元格内容。
>
> num_digits表示需要取多少位的参数。
>
> num_digits>0时，表示取小数点后对应位数的四舍五入数值。
>
> num_digits=0时，表示则将数字四舍五入到最接近的整数。
>
> num_digits< 0时，表示对小数点左侧前几位进行四舍五入。

1、对指定单元格进行四舍五入

```excel
=ROUND(E7,0)
```

### 9、排名次函数RANK()

> 返回一列数字的数字排位。 数字的排位是相对于列表中的其他值的大小。

语法：RANK(number,ref,[order])

> RANK 函数语法具有下列参数：
>
> - **Number** 必需。 要找到其排位的数字。
>
> - **Ref** 必需。 数字列表的数组，对数字列表的引用。 Ref 中的非数字值会被忽略。
>
> - **Order** 可选。 一个指定数字排位方式的数字。
>
>   如果 order 为 0（零）或省略，Microsoft Excel 对数字的排位是基于 ref 为按照降序排列的列表。
>
>   如果 order 不为零，Microsoft Excel 对数字的排位是基于 ref 为按照升序排列的列表。

1、获取指定单元格在范围内进行排名

```excel
=RANK(C3,C2:C11)
```

### 9、排名次函数RANK.EQ()

```
与RANK函数用法一致
```

> 返回一列数字的数字排位。 其大小与列表中其他值相关；如果多个值具有相同的排位，则返回该组值的最高排位。
>
> 如果要对列表进行排序，则数字排位可作为其位置。

语法

> RANK.EQ(number,ref,[order])
>
> RANK.EQ 函数语法具有下列参数：
>
> - **Number** 必需。 要找到其排位的数字。
> - **Ref** 必需。 数字列表的数组，对数字列表的引用。 Ref 中的非数字值会被忽略。
> - **Order** 可选。 一个指定数字排位方式的数字。
>
> 【注意】
>
> - 如果 Order 为 0（零）或省略，Excel 对数字的排位是基于 Ref 为按降序排列的列表。
> - 如果 Order 不为零， Excel 对数字的排位是基于 Ref 为按照升序排列的列表。

1、升序排名

```excel
=RANK.EQ(C3,C2:C11,1)
```

2、降序排名(0可以省略)

```excel
=RANK.EQ(C3,C2:C11,0)
```

### 10、取整函数INT()

> 将数字向下舍入到最接近的整数。

1、对指定单元格进行取整，忽略小数位

```excel
=INT(E3)
```

### 11、求字符串长度函数LEN()

> 返回文本字符串中的字符个数
>
> 【注意】数字，字符，汉字都属于一个字符，包括小数点

1、对指定单元格获取长度

```excel
=LEN(E3)
```

### 12、左取字符串函数LEFT()

> 从文本字符串的第一个字符开始返回指定个数的字符

语法

> LEFT(text, [num_chars])
>
> 该函数语法具有下列参数：
>
> - **Text** 必需。 包含要提取的字符的文本字符串。
>
> - num_chars
>
>    
>
>   可选。 指定要由 LEFT 提取的字符的数量。
>
>   - num_chars 必须大于或等于零。
>   - 如果 num_chars 大于文本长度，则 LEFT 返回全部文本。
>   - 如果省略 num_chars，则假定其值为 1。

1、获取指定单元格从左开始的第一个字符

```excel
=LEFT(F2)
```

2、获取指定单元格从左开始的指定长度个数的字符

```excel
=LEFT(F2,3)
```

### 13、右取字符串函数RIGHT()

> 根据所指定的字符数返回文本字符串中最后一个或多个字符

语法

> RIGHT(text,[num_chars])
>
> RIGHT 函数具有下列参数：
>
> - **文本** 必需。 包含要提取字符的文本字符串。
> - **num_chars** 可选。 指定希望 RIGHT 提取的字符数。
> - Num_chars 必须大于或等于零。
> - 如果 num_chars 大于文本长度，则 RIGHT 返回所有文本。
> - 如果省略 num_chars，则假定其值为 1。

1、获取指定单元格从右开始的第一个字符

```excel
=RIGHT(F2)
```

2、获取指定单元格从左开始的指定长度个数的字符

```excel
=RIGHT(F2,3)
```

### 14、日函数DAY()

> 返回以序列数表示的某日期的天数。 天数是介于 1 到 31 之间的整数。

语法

> DAY(serial_number)
>
> DAY 函数语法具有下列参数：
>
> - **Serial_number** 必需。 尝试查找的日期应使用 DATE 函数输入日期，或者将日期作为其他公式或函数的结果输入。 例如，使用函数 DATE(2008,5,23) 输入 2008 年 5 月 23 日。 如果[日期以文本形式输入](https://support.microsoft.com/zh-cn/office/更改日期系统、格式或两位数年份表示方式-aaa2159b-4ae8-4651-8bce-d4707bc9fb9f)，则会出现问题。

用法

| **日期**  |                             |          |
| --------- | --------------------------- | -------- |
| 2011-4-15 |                             |          |
| **公式**  | **描述（结果）**            | **结果** |
| =DAY(A2)  | 单元格 A2 (15) 中日期的天数 | 15       |

### 15、月函数MONTH()

> 返回日期（以序列数表示）中的月份。 月份是介于 1（一月）到 12（十二月）之间的整数。

语法

> MONTH(serial_number)
>
> MONTH 函数语法具有下列参数：
>
> - **Serial_number** 必需。 尝试查找的月份的日期应使用 DATE 函数输入日期，或者将日期作为其他公式或函数的结果输入。 例如，使用函数 DATE(2008,5,23) 输入 2008 年 5 月 23 日。 如果[日期以文本形式输入](https://support.microsoft.com/zh-cn/office/更改日期系统、格式或两位数年份表示方式-aaa2159b-4ae8-4651-8bce-d4707bc9fb9f)，则会出现问题。

用法

| **日期**   |                        |          |
| ---------- | ---------------------- | -------- |
| 2011-4-15  |                        |          |
| **公式**   | **说明**               | **结果** |
| =MONTH(A2) | 单元格 A2 中日期的月份 | 4        |

### 16、年函数YEAR()

> 返回对应于某个日期的年份。 Year 作为 1900 - 9999 之间的整数返回。

语法

> YEAR(serial_number)
>
> YEAR 函数语法具有下列参数：
>
> - **Serial_number** 必需。 要查找的年份的日期。 应使用 DATE 函数输入日期，或者将日期作为其他公式或函数的结果输入。 例如，使用函数 DATE(2008,5,23) 输入 2008 年 5 月 23 日。 如果日期以文本形式输入，则会出现问题。

用法

| **日期**  |                               |          |
| --------- | ----------------------------- | -------- |
| 2008-7-5  |                               |          |
| 2010-7-5  |                               |          |
| **公式**  | **描述（结果）**              | **结果** |
| =YEAR(A3) | 单元格 A3 中日期的年份 (2008) | 2008     |
| =YEAR(A4) | 单元格 A4 中日期的年份 (2010) | 2010     |

### 17、星期函数WEEKDAY()

> 返回对应于某个日期的一周中的第几天。 默认情况下，天数是 1（星期日）到 7（星期六）范围内的整数。

语法

> WEEKDAY(serial_number,[return_type])
>
> WEEKDAY 函数语法具有下列参数：
>
> - **Serial_number** 必需。 一个序列号，代表尝试查找的那一天的日期。 应使用 DATE 函数输入日期，或者将日期作为其他公式或函数的结果输入。 例如，使用函数 DATE(2008,5,23) 输入 2008 年 5 月 23 日。 如果日期以文本形式输入，则会出现问题。
> - **Return_type** 可选。 用于确定返回值类型的数字。
>
> | **Return_type** | **返回的数字**                                               |
> | --------------- | ------------------------------------------------------------ |
> | 1 或省略        | 数字 1（星期日）到 7（星期六）。 同 Microsoft Excel 早期版本。 |
> | 2               | 数字 1（星期一）到 7（星期日）。                             |
> | 3               | 数字 0（星期一）到 6（星期日）。                             |
> | 11              | 数字 1（星期一）到 7（星期日）。                             |
> | 12              | 数字 1（星期二）到数字 7（星期一）。                         |
> | 13              | 数字 1（星期三）到数字 7（星期二）。                         |
> | 14              | 数字 1（星期四）到数字 7（星期三）。                         |
> | 15              | 数字 1（星期五）到数字 7（星期四）。                         |
> | 16              | 数字 1（星期六）到数字 7（星期五）。                         |
> | 17              | 数字 1（星期日）到 7（星期六）。                             |

备注

> - Microsoft Excel 可将日期存储为可用于计算的序列号。 默认情况下，1900 年 1 月 1 日的序列号是 1，而 2008 年 1 月 1 日的序列号是 39448，这是因为它距 1900 年 1 月 1 日有 39448 天。
> - 如果当前日期基值的 serial_number 超出范围，则 #NUM！ 返回错误。
> - 如果 return_type 超出了上表中指定的范围，则 #NUM！ 返回错误。

用法

| **数据**        |                                                            |          |
| --------------- | ---------------------------------------------------------- | -------- |
| 2008-2-14       |                                                            |          |
| **公式**        | **描述（结果）**                                           | **结果** |
| =WEEKDAY(A2)    | 使用数字 1（星期日）到 7（星期六）表示的一周中的第几天 (5) | 5        |
| =WEEKDAY(A2, 2) | 使用数字 1（星期一）到 7（星期日）表示的一周中的第几天 (4) | 4        |
| =WEEKDAY(A2, 3) | 使用数字 0（星期一）到 6（星期日）表示的一周中的第几天 (3) | 3        |

### 18、日期函数 DATE()

> 返回表示特定日期的连续序列号。

语法：

> DATE(year,month,day)
>
> DATE 函数语法具有下列参数：
>
> - **Year** ：必需。***year\*** 参数的值可以包含一到四位数字。Excel 将根据计算机正在使用的日期系统来解释 ***year\*** 参数。默认情况下，Microsoft Excel for Windows 使用的是 1900 日期系统，这表示第一个日期为 1900 年 1 月 1 日。
>
> **提示:** 为避免出现意外结果，请对 ***year\*** 参数使用四位数字。例如，“07”可能意味着“1907”或“2007”。因此，使用四位数的年份可避免混淆。
>
> - 如果 ***year\*** 介于 0（零）到 1899 之间（包含这两个值），则 Excel 会将该值与 1900 相加来计算年份。例如，DATE(108,1,2) 返回 2008 年 1 月 2 日 (1900+108)。
> - 如果 ***year\*** 介于 1900 到 9999 之间（包含这两个值），则 Excel 将使用该数值作为年份。例如，DATE(2008,1,2) 将返回 2008 年 1 月 2 日。
> - 如果 ***year\*** 小于 0 或大于等于 10000，则 Excel 返回 错误值 #NUM!。
> - **Month** 必需。一个正整数或负整数，表示一年中从 1 月至 12 月（一月到十二月）的各个月。
> - 如果 ***month\*** 大于 12，则 ***month\*** 会从指定年份的第一个月开始加上该月份数。例如，DATE(2008,14,2) 返回表示 2009 年 2 月 2 日的序列数。
> - 如果 ***month\*** 小于 1，则 ***month\*** 会从指定年份的第一个月开始减去该月份数，然后再加上 1 个月。例如，DATE(2008,-3,2) 返回表示 2007 年 9 月 2 日的序列号。
> - **Day** 必需。一个正整数或负整数，表示一月中从 1 日到 31 日的各天。
> - 如果 ***day\*** 大于指定月中的天数，则 ***day\*** 会从该月的第一天开始加上该天数。例如，DATE(2008,1,35) 返回表示 2008 年 2 月 4 日的序列数。
> - 如果 ***day\*** 小于 1，则 ***day\*** 从指定月份的第一天开始减去该天数，然后再加上 1 天。例如，DATE(2008,1,-15) 返回表示 2007 年 12 月 16 日的序列号。
>
> **注意:** Excel 可将日期存储为连续序列号，以便能在计算中使用它们。1900 年 1 月 1 日的序列号为 1，2008 年 1 月 1 日的序列号为 39448，这是因为它与 1900 年 1 月 1 日之间相差 39,447 天。需要更改数字格式（设置单元格格式）以显示正确的日期。

用法

**=DATE(C2,A2,B2)** 将单元格 C2 中的年、单元格 A2 中的月以及单元格 B2 中的日合并在一起，并将它们放入一个单元格内作为日期。

```excel
=DATE(C2,A2,B2)
```