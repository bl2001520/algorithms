# 剑指offer 05.替换空格

请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。

## 解法1 双指针法

```java
// 很多数组填充类的问题,都可以事先给数组扩容到填充后的大小,然后从后向前操作,可以避免从前向后操作时的元素移动问题.
class Solution {
    public String replaceSpace(String s) {
        if (s == null || s.length() == 0) {
            return s;
        }
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            // 使用一个对象储存额外空间(需要扩充的空间)
            if (s.charAt(i) == ' ') {
                sb.append("  ");
            }
        }
        if (sb.length() == 0) {
            return s;
        }
        // 左指针指向原始字符串最后一个位置
        int left = s.length() - 1;
        // 扩充原始字符串
        s += sb;
        // 右指针指向新字符串最后一个位置
        int right = s.length() - 1;
        char[] ch = s.toCharArray();
        while (left < right) {
            if (ch[left] == ' ') {
                ch[right--] = '0';
                ch[right--] = '2';
                ch[right] = '%';
            } else {
                ch[right] = ch[left];
            }
            left--;
            right--;
        }
        return new String(ch);
    }
}
```

## 解法2

```java
// 使用一个新的对象复制
class Solution {
    public String replaceSpace(String s) {
        if (s == null || s.length() == 0) {
            return s;
        }
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == ' ') {
                sb.append("%20");
            } else {
                sb.append(s.charAt(i));
            }
        }
        return sb.toString();
    }
}
```

## 解法3

```java
// 库函数
class Solution {
    public String replaceSpace(String s) {
        return s.replace(" ", "%20");
    }
}
```

