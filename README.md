202083
387. 字符串中的第一个唯一字符
     给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。 
题解：
class Solution {
    public int firstUniqChar(String s) {
        //字符串转化为字符数组
        char []a = s.toCharArray();
        //定义一个数组来记录每个字符出现的次数
        int [] count = new int[26];
        //此写法为遍历数组的便捷写法
        for(char c : a){
        //c-'a'把字符转化为0-25，c中字符没出现一次count数组记录加一
            count[c - 'a']++;
        }
        //遍历字符串找到第一个count数组值为1的下标
        for(int i = 0;i < s.length();i++){
            if(count[a[i] - 'a'] == 1)
                return i;
        }
        return -1;
    }
}
389. 找不同
     给定两个字符串 s 和 t，它们只包含小写字母。字符串 t 由字符串 s 随机重排，然后在随机位置添加一个字母。请找出在 t 中被添加的字母。
题解：
class Solution {
    public char findTheDifference(String s, String t) {
        char ans = 0;
        for(int i = 0;i < s.length();i++)
            ans ^= s.charAt(i);
        for(int i = 0;i < t.length();i++)
            ans ^= t.charAt(i);
        return ans;
    }
}
知识点：此题利用了异或运算，相同字符异或操作后为0,0^x(任何数)=x,不管两个相同的数以什么顺序异或最终结果都为0，所以s和t中相同的字符都存在两个，将它们全都异或之后为0，最后多出来一个即为结果。

392. 判断子序列
     给定字符串 s 和 t ，判断 s 是否为 t 的子序列。你可以认为 s 和 t 中仅包含英文小写字母。字符串 t 可能会很长（长度 ~= 500,000），而 s 是个短字符串（长度 <=100）。字符串的一个子序列是原始字          符串删除一些（也可以不删除）字符而不改变剩余字符相对位置形成的新字符串。（例如，"ace"是"abcde"的一个子序列，而"aec"不是）。
     题解:
class Solution {
    public boolean isSubsequence(String s, String t) {
        int n = s.length(),m = t.length();
        int i = 0,j = 0;
        while(i < n && j < m){
            if(s.charAt(i) == t.charAt(j))
                i++;
            j++;
        }
        return i == n;
    }
}
本题使用双指针，初始化两个指针i和j，分别指向s和t的初始位置。每次贪心地匹配，匹配成功则i和j同时右移，匹配s的下一个位置，匹配失败则j右移，i不变，尝试用t的下一个字符匹配s。最终如果i移动到s的末尾，就说明s是t的子序列。
