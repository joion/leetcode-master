## 题目地址 
https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/

## 思路 

如果想把这道题目做到极致，就不要只用额外的辅助空间，先扩充数组到每个空格替换成"%20"之后的大小
然后从后向前替换空格，双指针法：

思路如下： 
<video src="../video/替换空格.mp4" controls="controls" width="640" height="320" autoplay="autoplay">
Your browser does not support the video tag.
</video>

时间复杂度，空间复杂度均超过100%的用户 

<img src='../pics/剑指Offer05.替换空格.png' width=600> </img></div>

## C++代码 


```
class Solution {
public:
    string replaceSpace(string s) {
        int count = 0; // 统计空格的个数
        int sOldSize = s.size();
        for (int i = 0; i < s.size(); i++) {
            if (s[i] == ' ') {
                count++;
            }
        }
        // 扩充字符串s的大小，也就是每个空格替换成"%20"之后的大小
        s.resize(s.size() + count * 2);
        int sNewSize = s.size();
        // 从后先前将空格替换为"%20"
        for (int i = sNewSize - 1, j = sOldSize - 1; j < i; i--, j--) {
            if (s[j] != ' ') {
                s[i] = s[j];
            } else {
                s[i] = '0';
                s[i - 1] = '2';
                s[i - 2] = '%';
                i -= 2;
            }
        }
        return s;
    }
};

```
> 更过算法干货文章持续更新，可以微信搜索「代码随想录」第一时间围观，关注后，回复「Java」「C++」 「python」「简历模板」「数据结构与算法」等等，就可以获得我多年整理的学习资料。

