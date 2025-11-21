# pavlov_homework_fun_prog
## Задача 1 - Climbing Stairs
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
### Методология - Использование с помощью рекурсии включающей запоминание промежуточных результатов (мемоизацию), что является реализацией динамического программирования
