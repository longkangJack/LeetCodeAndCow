# 剑指offer-8

> ### 题目描述
>
> 一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。

> 题目分析:
>
> 与斐波那契数列类似,当number为0，1，2时候返回本身，当number大于2时，返回该数的后两位数字相加.

```cpp
//非递归
class Solution {
public:
    int jumpFloor(int number) {
        vector<int> v(number+1);
        v[0]=0;
        v[1]=1;
        v[2]=2;
        for(int i=3;i<=number;++i)
        {
            v[i] = v[i-1]+v[i-2];
        }
        return v[number];
    }
};
//递归算法
class Solution {
public:
    int jumpFloor(int number) {
        if(number<=2)
            return number;
        else 
        {
            return jumpFloor(number-1)+jumpFloor(number-2);
        }
    }
};
```

