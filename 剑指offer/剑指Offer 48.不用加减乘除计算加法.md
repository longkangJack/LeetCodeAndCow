## 剑指Offer48-不用加减乘除计算加法

### 题目描述

写一个函数，求两个整数之和，要求在函数体内不得使用+、-、*、/四则运算符号。

分析：注意测试用例里面可能有期中有个数为0的情况这样while循环会直接跳出去，所以先判断下。

```cpp
class Solution {
public:
    int Add(int num1, int num2)
    {
        int sum,carry;
        if(num2 == 0)
        {
            num2 = num1;
            num1 = 0;
        }
        while(num2)
        {
            sum = num1^num2;
            carry = (num1&num2)<<1;
            num1 = sum;
            num2 = carry;
        }
        return sum;
    }
};
```

