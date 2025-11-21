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
### Методология - Решение с помощью рекурсии включающей запоминание промежуточных результатов (мемоизацию), что является реализацией динамического программирования

***

## Задача 2 - Jumping Game 2
```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        steps = 0
        index_max_step = 0
        max_step = 0

        for i in range(len(nums) - 1):
            max_step = max(max_step, i + nums[i])
            if i == index_max_step:
                steps += 1
                index_max_step = max_step
                if index_max_step >= len(nums) - 1:
                    break

        return steps
```
### Методология - Решение с помощью жадного алгоритма
При обходе массива слева направо отслеживаются:

- <kbd>max_step</kbd> — максимально дальний индекс, которого можно достигнуть с текущего и предыдущих элементов.

- <kbd>index_max_step</kbd> — граница текущего прыжка, после достижения которой нужно сделать следующий прыжок.

- Счётчик прыжков <kbd>steps</kbd> увеличивается при достижении границы прыжка.

***

## Задача 3 - Pascal’s Triangle 2
```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        paskal_str = [1]

        for i in range(1, rowIndex + 1):
            paskal_str.append(paskal_str[-1] * (rowIndex - i + 1) // i)

        return paskal_str
```
### Методология - основывается на вычислении элементов строки через биномиальные коэффициенты

***

## Задача 4 - Best time to buy and sell stock 1
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        min_price = 10001
        max_stonks = 0

        for price in prices:
            if price < min_price: min_price = price
            else: max_stonks = max(max_stonks, price - min_price)
        return max_stonks
```
### Методология - Решение с помощью жадного алгоритма
- При обходе каждого значения <kbd>price</kbd> по массиву <kbd>prices</kbd> выполняется сравнение с <kbd>min_price</kbd>.

- Если текущая цена меньше <kbd>min_price</kbd>, значит, найден новый минимум (лучшая цена для покупки), и <kbd>min_price</kbd> обновляется.

- Если цена выше или равна <kbd>min_price</kbd>, считается потенциальная прибыль <kbd>price</kbd> - <kbd>min_price</kbd>. Если она больше текущей максимальной прибыли, обновляем <kbd>max_stonks</kbd>.
***
