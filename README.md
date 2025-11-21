# pavlov_homework_fun_prog
```python
class Solution:
    def climbStairs(self, n: int) -> int:
        arr = [0] * 45
        arr[0] = 1
        arr[1] = 2

        def fun(n, arr):
            if arr[n-1] == 0: 
                arr[n-1] = fun(n-1, arr) + fun(n-2, arr)
            return arr[n-1]

        return fun(n, arr)
```
