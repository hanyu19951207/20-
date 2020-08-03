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
