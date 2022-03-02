# 剑指offer 58-2.左旋转字符串

```java
// 先翻转前n个字符，再反转后面字符，最后翻转整个字符
class Solution {
    public String reverseLeftWords(String s, int n) {
        char[] chars = s.toCharArray();
        reverse(chars, 0, n - 1);
        reverse(chars, n, chars.length - 1);
        reverse(chars, 0, chars.length - 1);
        return new String(chars);
    }

    private char[] reverse(char[] chars, int l, int r) {
        while (l < r) {
            chars[l] ^= chars[r];
            chars[r] ^= chars[l];
            chars[l] ^= chars[r];
            l++;
            r--;
        }
        return chars;
    }
}
```

