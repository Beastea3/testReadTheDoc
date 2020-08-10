# Backtracking Algorithm

[Backtracking by D.Matuszek](https://www.cis.upenn.edu/~matuszek/cit594-2012/Pages/backtracking.html);

```
给定一个只包含数字的字符串，复原它并返回所有可能的 IP 地址格式。

有效的 IP 地址正好由四个整数（每个整数位于 0 到 255 之间组成），整数之间用 '.' 分隔。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/restore-ip-addresses
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```
### Solution:
```javascript
const restoreIpAddresses = (s) => {
  const res = [];
  const dfs = (subRes, startIdx) => {
    // Found
    if (subRes.length === 4 && startIdx === s.length) {
      res.push(subRes.join('.'));
      return;
    }

    // When Found 4 segments, but some chars remained.
    if (subRes.length === 4 && startIdx < s.length) {
      return;
    }

    for (let len = 1; len <= 3; len += 1) {
      // Note: charAt return '' if exceeds the range of the string
      if (s.charAt(startIdx + len - 1) == '') {
        return;
      } 
      if (len != 1 && s.charAt(startIdx) == '0') {
        return;
      }
      const subString = s.substring(startIdx, startIdx + len);
      if (len === 3 && +subString > 255) return;
      subRes.push(subString);
      dfs(subRes, startIdx + len);
      subRes.pop();
    }
  }
  dfs([], 0);
  return res;
};
```


Backtracking is a form of recursion, and Backtrack is even not an algorithm but a control structure. Which enable a program to run backward. With Backtracking, the program will find the correct answer or the best result which u want to achieve.

![img](./treesearch.gif);

The steps below is to find a good leaf in a tree;

1. Starting at Root, your options are A and B, and suppose A is chosen;
2. At A node, suppose we choose C as the next node to check;
3. C is not a good leaf, then go back to A node;
4. As D is not checked yet, we check D;
5. D is a bad leaf too, so we go back, as A has no other options, so we go back to the parent of A, the Root;
6. B is not checked, try the leaves of B;
7. E is a good leaf, find it.

Actually, when we do have a tree structure to do sth like backtracking, this kind of backtracking could be called `dfs` (depth-first-searching);

Below is a basic backtracking pseudo code:

```
boolean solve(Node n) {
    if n is a leaf node {
        if the leaf is a goal node, return true
        else return false
    } else {
        for each child c of n {
            if solve(c) succeeds, return true
        }
        return false
    }
}
```

Of course, we can also write backtracking without recursion, but with a stack;

```
boolean solve(Node n) {
    put node n on the stack;
    while the stack is not empty {
        if the node at the top of the stack is a leaf {
            if it is a goal node, return true
            else pop it off the stack
        }
        else {
            if the node at the top of the stack has untried children
                push the next untried child onto the stack
            else pop the node off the stack

    }
    return false
}
```

## 3 Key Points in Backtracking

### Selection

Abstracting problem into selections;

### Restriction

Pruning invalid routine to get the correct answer;

### Goal

Collect the answers which match our goal;

And in the problem above, the IP problem.

1. We need to abstract the problem into backtracking selections:
  * Select the sub-string to construct IP segment;
  * Select different length of sub-string to construct IP segment;

2. We have to restrict our results;
  * The string should not started with '0';
  * The segment's length should between 1 and 3;
  * The value of an IP segment should not exceed 255;
  * When the 4 IP segments constructed, no characters should be remaining.

3. Collect the results with the restrictions above, these results should be the answer of the problem;


