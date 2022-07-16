### 1. 字符串能否重排

给定两个字符串 s1 和 s2，请编写一个程序，确定其中一个字符串的字符重新排列后，能否变成另一个字符串。

1. 示例 1

   输入: s1 = "abc", s2 = "bca"

   输出: true 

2. 示例 2

   输入: s1 = "abc", s2 = "bad"

   输出: false

说明：

- 0 <= len(s1) <= 100
- 0 <= len(s2) <= 100



#### 解法

一般思路就是利用哈希表记录字符以及各个字符的数量，两个字符串能重排得到相同的字符，则两个字符串的字符以及字符数量均相等。遍历两个字符串，判断两个字符串能否重排。

另一种思路就是将两个字符串以字符数组的形式保存，再进行排序。同步遍历两个排序后的数组，若出现字符不一致的情况，则判定不能重排即可。

```java
public boolean CheckPermutation(String s1, String s2) {
    if(s1.length() != s2.length()) {
        return false;
    }
    char ch;
    HashMap<Character, Integer> chars = new HashMap<Character, Integer>();
    for (int i = 0; i < s1.length(); i++) {
        ch = s1.charAt(i);
        // Java 的哈希表不能直接修改值，只能以 put 的形式来进行修改
        chars.put(ch, chars.getOrDefault(ch,0)+1);
    }
    for (int i = 0; i < s2.length(); i++) {
        ch = s2.charAt(i);
        chars.put(ch, chars.getOrDefault(ch,0)-1);
    }
    for(int x: chars.values()) {
        if (x != 0) {
            return false;
        }
    }
    return true;
}

```

---



### 2. 第一个只出现一次的字符

在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

1. 示例 1

   输入：s = "abaccdeff"

   输出：'b'

2. 示例 2

   输入：s = "" 

   输出：' '



#### 解法：类哈希思想

一般的解法便是建立一个哈希表，遍历字符串，利用键存储出现的字符，值存储字符出现的次数，然后在此遍历字符串，针对遍历到的字符，如果其在哈希表中对应的值为 1，则返回该字符。

但是，题中已经明确字符串只包含小写字符，因此，可以使用长度为 26 的整型数组代替哈希表。步骤如下。

1. 创建整型数组 count，遍历字符串，记录每个字符出现的次数。
2. 遍历字符串，针对遍历到的字符，查看 count 中其出现的次数，若为 1，返回该字符。

```java
public char firstUniqChar(String s) {
    int[] count = new int[26];
    char[] chars = s.toCharArray();
    for (char c : chars) {
        count[c - 'a']++;
    }
    for (char c : chars) {
        if (count[c-'a'] == 1) {
            return c;
        }
    }
    return ' ';
}

```

---



### 3. 两数之和

给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。你可以按任意顺序返回答案。

1. 示例 1

   输入：nums = [2,7,11,15], target = 9

   输出：[0,1]

   解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。

2. 示例 2

   输入：nums = [3,2,4], target = 6

   输出：[1,2]



#### 解法：哈希表

利用哈希表保存已经遍历过的数字及其索引。

遍历数组，针对当前遍历的数字 $num$：

1. 如果 $target-num$ 存在于哈希表中，则返回对应的键值以及 num 的索引值。
2. 如果不存在，以 num 为键，索引值为值存入哈希表中。

```java
public int[] twoSum(int[] nums, int target) {;
    HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
    for (int i = 0; i < nums.length; i++) {
        if (map.containsKey(target-nums[i])) {
            return new int[]{i, map.get(target-nums[i])};
        } else {
            map.put(nums[i], i);
        }
    }
    return new int[]{};
}

```

---

