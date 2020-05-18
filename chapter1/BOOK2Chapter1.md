猜数游戏

:one: if语句的结构/效率/可读性

:two:do语句

:three:for语句

:four:break语句

:five:相等运算符和关系运算符

:six:逻辑运算符

:seven:增量运算符(前置/后置)

:eight:sizeof运算符

:nine:表达式求值

:keycap_ten:德·摩根定律

:one::one:随机数的生成与种子的变更

:one::two:对象宏

:one::three:数组

:one::four:数组的遍历

:one::five:数组元素的初始化

:one::six:数组元素个数的设定和获取

## 1. 猜数判定

显示键盘输入的值和计算机事先准备好的数字比较结果

## 2. 重复到猜到为止

## 3. 随机设定目标数字

**rand函数**：生成随机数

#include<stdlib.h>

int rand(void);

功能：计算0~RAND_MAX的伪随机整数序列

返回值 返回生成的伪随机数整数

最小值为0；

最大值取决于编译环境，所以用头文件<stdlib.h>将其定义为一个名为RAND_MAX的对象宏

#define RAND_MAX 32767

```c
	do {
		printf("生成的随机数是：%d\n", rand());
		printf("retry? NO --- [0]   YES ---[1]\n");
		scanf_s("%d", &retry);
	} while (retry == 1);
```



**srand函数**：设置用于生成随机数的种子

rand函数对一个叫做”种子“的基准值加以运算来生成随机数的。

rand函数的默认种子是**常量1**。所以生成同一个随机数序列

要生成不同的随机数序列，就必须要改变种子的值



srand

#include<stdlib.h>

void srand(unsigned seed);



rand **伪随机数** 看起来像随机数，确实基于某种规律的





方法 ：把运行程序的时间当作种子。

```c
	srand(time(NULL));
	do {
		printf("生成的随机数：%d\n", rand());

		printf("retry???\tNO --- [0] YES --- [1]\n\n");
		scanf_s("%d", &retry);

	} while (retry == 1);
```





**生成某个特定范围内的随机数**

- *rand() % 11* 		//生成大于等于0且小于等于10的随机数*

- *1 + rand() % 999* 		//生成1 ~ 999（0 + 1 ~ 998 + 1）的随机数

- *100 + rand() % 900*        //生成3位数的整数100 ~ 999 （0 + 100 ~ 899 + 100）

## 小结

- 第一步 准备工作：

生成随机数之前要基于当前时间设定”种子“的值

srand(time(NULL));



- 第二步 生成随机数：

rand()



**限制输入次数**

