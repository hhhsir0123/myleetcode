







# 标题

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

