## 2. Add two numbers

- Notice that the digits of two numbers could be different;
- The carry must be stored if the sum of one digit greater than 10;

Solotion:

```java
public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    ListNode result = new ListNode(0);
    ListNode p = l1, q = l2, cur = result;
    
    int carry = 0;
    while (p != null || q != null) {
        int x = p != null ? p.val : 0;
        int y = q != null ? q.val : 0;
        int sum = carry + x + y;
        carry = sum / 10;
        cur.next = new ListNode(sum % 10);
        cur = cur.next;
        if (p != null) p = p.next;
        if (q != null) q = q.next;
    }
    if (carry > 0) {
        cur.next = new ListNode(carry);
    }
    return result.next;
}
```


## 3. Longest Substring Without Repeating Characters

- The time Complexity of brute force could be O(n^3);
- HashMap solution's time complexity is O(n) and space complexity is O(n);
- If char set is known, the space complexity could be O(min(m, n))(m is the amount of the char set);

Solotion:

```java
public int lengthOfLongestSubstring(String s) {
    HashMap<Character, Integer> charMap = new HashMap<>();
    int len = s.length();
    int ans = 0;
    for(int l = 0, r = 0; r < len; r++) {
        if(charMap.containsKey(s.charAt(r))) {
            l = Math.max(l, charMap.get(s.charAt(r)));
        }
        ans = Math.max(ans, r - l + 1);
        charMap.put(s.charAt(r), r + 1);
    }
    return ans;
}
```

## 4. 寻找两个有序数组的中位数

> 给定两个大小为 m 和 n 的有序数组 nums1 和 nums2。

> 请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))。

> 你可以假设 nums1 和 nums2 不会同时为空。

> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/median-of-two-sorted-arrays
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

这题有多种解法，暴力一点的就是归并排序，然后选出中位数，时间复杂度为O(n + m)，更好一点的方法是可以用二分查找，可以把时间复杂度降到O(log(m + n));
代码如下：

```java
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int m = nums1.length;
        int n = nums2.length;
        int left = (m + n + 1) / 2;
        int right = (m + n + 2) / 2;
        return (getKthMin(nums1, 0, m - 1, nums2, 0, n - 1, left)
            + getKthMin(nums1, 0, m - 1, nums2, 0, n - 1, right)) * 0.5;
    }

    int getKthMin(int[] nums1, int start1, int end1, int[]nums2, int start2, int end2, int k) {
        int len1 = end1 - start1 + 1, len2 = end2 - start2 + 1;
        if (len1 > len2) {
            return getKthMin(nums2, start2, end2, nums1, start1, end1, k);
        }
        if(len1 == 0) return nums2[start2 + k - 1];
        if(k == 1) return Math.min(nums1[start1], nums2[start2]);

        int index1 = Math.min((k / 2) - 1 + start1, end1);
        int index2 = Math.min((k / 2) - 1 + start2, end2);

        if (nums1[index1] < nums2[index2]) {
            return getKthMin(nums1, index1 + 1, end1, nums2, start2, end2, k - (index1 - start1 + 1));
        } else {
            return getKthMin(nums1, start1, end1, nums2, index2 + 1, end2, k - (index2 - start2 + 1));
        }
    }
```

## 5. Longest Palindromic Substring

- The time Complexity of dp is O(n^2) and space complexity is O(n^2) too;
- Expand around center needs only O(1) space complexity;

Solotion(dp):

```java
    public String longestPalindrome(String s) {
        int n = s.length();
        boolean[][] dp = new boolean[n][n];
        String res = "";
        for(int i = n - 1; i >= 0; i--) {
            for(int j = i; j < n; j++) {
                dp[i][j] = s.charAt(i) == s.charAt(j) && (j - i < 3 || dp[i+1][j-1]); 
                if(dp[i][j] && res.length() <= j - i + 1) {
                    res = s.substring(i, j + 1);
                }
            }
        }
        return res;
    }
```

Solution(Expand Around):

```java
public String longestPalindrome(String s) {
    if (s == null || s.length() < 1) return "";
    int start = 0, end = 0;
    for (int i = 0; i < s.length(); i++) {
        int len1 = expandAroundCenter(s, i, i);
        int len2 = expandAroundCenter(s, i, i + 1);
        int len = Math.max(len1, len2);
        if (len > end - start) {
            start = i - (len - 1) / 2;
            end = i + len / 2;
        }
    }
    return s.substring(start, end + 1);
}

private int expandAroundCenter(String s, int left, int right) {
    int L = left, R = right;
    while (L >= 0 && R < s.length() && s.charAt(L) == s.charAt(R)) {
        L--;
        R++;
    }
    return R - L - 1;
}
```

## 1004.Max Consecutive Ones III

Given an array A of 0s and 1s, we may change up to K values from 0 to 1.

Return the length of the longest (contiguous) subarray that contains only 1s. 

Solution of DP:
```java
public int longestOnes(int[] A, int K) {
    int zeroCount=0,start=0,res=0;
    for(int end=0;end<A.length;end++){
        if(A[end] == 0) zeroCount++;
        while(zeroCount > K){
            if(A[start] == 0) zeroCount--;
            start++;
        }
        res=Math.max(res,end-start+1);
    }
    return res;
}
```

And a short but comprehensive solution:

```java
public int longestOnes(int[] A, int K) {
    int i = 0, j;
    for(j = 0; j < A.length; j++) {
        if(A[j] == 0) K--;
        if(K < 0 && A[i++] == 0) {
            K++;
        }
    }
    return j - i;
}
```
>  as you can see from the code, j is constantly moving right. K here can be considered as the remaining feasible amount of flips, and reflects the current range (i.e., from i to j). When K<0, it's not a feasible solution and when K>=0, it'll be a feasible solution. If currently range is not yet a feasible solution or better than current "memory" frame (i.e., K<0 judgement) , i will try follow up the j and j-i (the frame size) remains unchanged, keeping the current maximum size intact. Whenever the flip count K of current range (i.e., still i to j) is greater or equals to 0, it means we can possibly expand our frame, and that's exactly what the code does. (i remains unchanged since it will not goes into K<0 clauses, and j keeps moving when K>=0). Eventually, when j comes to the end, the "memory" frame will automatically (by design of course) give us the maximum range throughout the array.
> -- ywen1995


Notice that i, j are not the real index of the original A;


## Atoi
请你来实现一个 atoi 函数，使其能将字符串转换成整数。

首先，该函数会根据需要丢弃无用的开头空格字符，直到寻找到第一个非空格的字符为止。接下来的转化规则如下：

如果第一个非空字符为正或者负号时，则将该符号与之后面尽可能多的连续数字字符组合起来，形成一个有符号整数。
假如第一个非空字符是数字，则直接将其与之后连续的数字字符组合起来，形成一个整数。
该字符串在有效的整数部分之后也可能会存在多余的字符，那么这些字符可以被忽略，它们对函数不应该造成影响。
注意：假如该字符串中的第一个非空格字符不是一个有效整数字符、字符串为空或字符串仅包含空白字符时，则你的函数不需要进行转换，即无法进行有效转换。

在任何情况下，若函数不能进行有效的转换时，请返回 0 。

这道题要注意边界的考量；
算法的话没什么难度；

```java
    public int myAtoi(String str) {
        int res = 0, min = Integer.MIN_VALUE, max = Integer.MAX_VALUE;
        int index = 0, ans = 0;
        boolean positive = true;
        while(index < str.length() && str.charAt(index) == ' ') {
            index++;
        }
        if(index == str.length()) return 0;
        if(str.charAt(index) == '+') {
            index++;
        } else if(str.charAt(index) == '-') {
            positive = false;
            index++;
        }    
        while(index < str.length() && isDigit(str.charAt(index))) {
            int digit = str.charAt(index) - '0';
            if(ans > (max - digit) / 10) {
                return positive ? max : min;
            }
            ans = ans * 10 + digit;
            index++;
        }
        return positive ? ans : (-1 * ans);
    }

    boolean isDigit(char c) {
        return c <= '9' && c >= '0';
    }
```

## 11. 盛最多水的容器
比较经典的滑动窗口问题，滑动窗口取得最优解，双指针问题；

```java
   public int maxArea(int[] height) {
        int l = 0, r = height.length - 1, area = 0;
        while(l < r) {
            area = Math.max(Math.min(height[l], height[r]) * (r - l), area);
            if(height[l] < height[r]) {
                l++;
            } else {
                r--;
            }
        }
        return area;
    }
```

## 12. 整数转罗马数字
使用贪心算法，有点像找零时用到的方式，不停尝试最短距离，在这道题里，就是去尝试最大的数字；

```java
    public String intToRoman(int num) {
        int[] nums = new int[]{ 1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        String[] romans = new String[]{"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        int index = 0;
        StringBuilder s = new StringBuilder();
        while(num > 0) {
            if(num >= nums[index]) {
                num -= nums[index];
                s.append(romans[index]);
            } else {
                index++;
            }
        }
        return s.toString();
    }
```

## 14. 最长公共前缀

```java
    public String longestCommonPrefix(String[] strs) {
        int amount = strs.length;
        if (amount == 0) return "";
        String temp = strs[0];
        for(int i = 0; i < temp.length(); i++) {
            char c = temp.charAt(i);
            for(int j = 1; j < amount; j++) {
                if (i > strs[j].length() - 1 || strs[j].charAt(i) != c) {
                    return temp.substring(0, i);
                }
            }
        }
        return temp;
    }
```

## 15. 三数之和

类似于两数之和，数组越界问题要处理好；

```java
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        if(nums.length < 3) return res;
        for(int i = 0; i < nums.length;i++) {
            if(nums[i] > 0) return res;
            if (i > 0 && nums[i] == nums[i - 1]) continue;
            int L = i + 1, R = nums.length - 1;
            while(L < R) {
                int sum = nums[L] + nums[R] + nums[i];
                if(sum < 0) {
                    L++;
                } else if(sum > 0) {
                    R--;
                } else {
                    res.add(Arrays.asList(nums[i], nums[L], nums[R]));
                    while(L < R && nums[L] == nums[L + 1]) {
                        L++;
                    }
                    while(L < R && nums[R] == nums[R - 1]) {
                        R--;
                    }
                    L++;
                    R--;
                }
            }
        }
        return res;
    }
```

## 16. 最接近的三数之和

和之前的三数之和很像，固定住一个数，然后找最接近的两数；

```java
public int threeSumClosest(int[] nums, int target) {
    Arrays.sort(nums);
    int diff = Integer.MAX_VALUE;
    int res = nums[0] + nums[1] + nums[2];
    for(int i = 0; i < nums.length;i++) {
        if (i > 0 && nums[i] == nums[i - 1]) continue;
        int L = i + 1, R = nums.length - 1;
        while(L < R) {
            int sum = nums[L] + nums[R] + nums[i];
            if(Math.abs(sum - target) < diff) {
                diff = Math.abs(sum - target);
                res = nums[L] + nums[R] + nums[i];
            }
            if(sum < target) {
                L++;
            } else if(sum > target) {
                R--;
            } else {
                return target;
            }
        }
    }
    return res;
}
```


