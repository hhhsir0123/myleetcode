







# 回文串

> 给你一个字符串 `s`，请你将 `s` 分割成一些 子串，使每个子串都是 **回文串** 。返回 `s` 所有可能的分割方案。
>
>  
>
> **示例 1：**
>
> ```
> 输入：s = "aab"
> 输出：[["a","a","b"],["aa","b"]]
> ```
>
> **示例 2：**
>
> ```
> 输入：s = "a"
> 输出：[["a"]]
> ```
>
>  
>
> **提示：**
>
> - `1 <= s.length <= 16`
> - `s` 仅由小写英文字母组成

**mycode**

```python3
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        rtn = list()

        def is_back_str(s, i, j):
            if i >= j:
                return True
            ii, jj = i, j
            while ii < jj:
                if s[ii] != s[jj]:
                    return False
                ii += 1
                jj -= 1
            return True

        def _partition(s, l):
            if not s:
                rtn.append([item for item in l])
                return
            for i in range(1,len(s) + 1):
                s1, s2 = s[:i], s[i:]
                if not is_back_str(s1, 0, len(s1) - 1):
                    continue
                l.append(s1)
                _partition(s2, l)
                l.pop()
        _partition(s, list())
        return rtn
```

**comment**

*还有更优解，todo*

------

# N皇后

按照国际象棋的规则，皇后可以攻击与之处在同一行或同一列或同一斜线上的棋子。

**n 皇后问题** 研究的是如何将 `n` 个皇后放置在 `n×n` 的棋盘上，并且使皇后彼此之间不能相互攻击。

给你一个整数 `n` ，返回所有不同的 **n 皇后问题** 的解决方案。

每一种解法包含一个不同的 **n 皇后问题** 的棋子放置方案，该方案中 `'Q'` 和 `'.'` 分别代表了皇后和空位。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2020/11/13/queens.jpg)

```
输入：n = 4
输出：[[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
解释：如上图所示，4 皇后问题存在两个不同的解法。
```

**示例 2：**
 

**mycode**

```python3
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        rtn = list()
        def generate_board():
            board = list()
            for i in range(n):
                row[queens[i]] = "Q"
                board.append("".join(row))
                row[queens[i]] = "."
            return board
        
        def _traceback(row):
            if row == n:
                board = generate_board()
                rtn.append(board)
            for i in range(n):
                if i in columns or row - i in diagonal1 or row + i in diagonal2:
                    continue
                queens[row] = i
                columns.add(i)
                diagonal1.add(row-i)
                diagonal2.add(row+i)
                _traceback(row+1)
                queens[row] = -1
                columns.remove(i)
                diagonal1.remove(row-i)
                diagonal2.remove(row+i)
        queens = [-1] * n
        columns = set()
        diagonal1 = set()
        diagonal2 = set()
        row = ["."] * n
        _traceback(0)
        return rtn
```

**comment**

*思路很简单，但需要自己能写*

------


