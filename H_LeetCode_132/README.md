# 题目名称：分割回文串2

## 题目链接：https://leetcode-cn.com/problems/palindrome-partitioning-ii/


## 题解：

给定字符串，用最少的分割次数将其分割成子串，且每个子串都是回文串。

与分割相关，算是分治问题，算是多步决策。那么是否有优化子结构？我们考虑前m个字符，如果我们确定在这里要进行分割，那么我们前m个字符一定是要取分割次数最少的方法，也即，要有优化子结构。OPT(1, N)=min(OPT(1, M)+OPT(M+1, N) + 1)。但是，这是只是能分治的结构、递归的结构，而且，我们不可能计算一个左边的就去计算右边的，我们应该从左边计算到底，迭代的结构。所以我们考虑的问题变成：如果我们知道了OPT(1, M)以左所有的OPT的值，如何计算OPT(1, M+1)？也就是，我们如何combine？我们希望新加入的值与前面的构成回文串，而且越长越好，那么就应该从第0个开始（即整个1到M+1）扫描，判断[i ,M+1]之间是不是回文串，是的话就返回OPT(1, M + 1)=OPT(1, i) + 1。很明显，我们最后要取的i应该是使得OPT(1, M + 1)最小，也就是OPT(1, i)最小的i。OPT(1, M + 1)=min(OPT(1, i) + 1)。这个式子与前面的差别就是，将OPT(M+1, N)变成了一个无需分割的回文串，所以为0。再换句话说，我们只是选取了比较好的M来简化计算，来避免重复计算。这道题的重点在于combine。
