# 题目名称：通配符匹配

## 题目链接：https://leetcode-cn.com/problems/wildcard-matching/


## 题解：

此题跟10正则表达式类似，但是此处是“？”通配一个字符，“*”通配任意长度（包括0）的字符串。而在10中，“_”通配一个字符，“*”通配前一个任意长度（包括0）的前一个字符。

所以一样的思路，“？”是不需要选择的，“？”就代表一定匹配。但是此处不考虑连续出现的问题，所以一次读进一个即可。（10中“*”表示多个重复，所以一次性多读入比较好）

这里的“*”与10中“_*”等价，所以问题就在于抉择“*”代表几个字符，所以这里要进行枚举，或者说，这就是多步决策，所以要用动态规划。

所以具体解法就是：挨个读入，相同或者有“？”则向后读入。如果遇到“*”就要进行多种情况的决策，取“且”操作。

解法中的贪心，实际上也一样的，只是不用空间存储，用回溯结构，但是，不存储，必然会导致遇到特殊结构时重复单元重复计算的问题。这里没有明显的贪心结构。