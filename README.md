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
<img width="1907" height="629" alt="image" src="https://github.com/user-attachments/assets/4fd3096c-51b5-4d59-a2f8-ea8bba66ea66" />

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
<img width="1920" height="626" alt="image" src="https://github.com/user-attachments/assets/76b64210-c90a-4df5-88de-372ba5eb10cf" />

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
<img width="1920" height="618" alt="image" src="https://github.com/user-attachments/assets/be549526-1af3-4516-a158-543794549f03" />

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
<img width="1920" height="616" alt="image" src="https://github.com/user-attachments/assets/aa46e78b-6e32-4183-87e8-4158578d647f" />

### Методология - Решение с помощью жадного алгоритма
- При обходе каждого значения <kbd>price</kbd> по массиву <kbd>prices</kbd> выполняется сравнение с <kbd>min_price</kbd>.

- Если текущая цена меньше <kbd>min_price</kbd>, значит, найден новый минимум (лучшая цена для покупки), и <kbd>min_price</kbd> обновляется.

- Если цена выше или равна <kbd>min_price</kbd>, считается потенциальная прибыль <kbd>price - min_price</kbd>. Если она больше текущей максимальной прибыли, обновляем <kbd>max_stonks</kbd>.

***

## Задача 5 - Best time to buy and sell stock 2
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        min_price = 10001
        max_price = 0
        stonks = 0
        for price in prices:

            if price < min_price and price >= max_price:
                min_price = price
            else:
                if max_price > price:
                    stonks += max_price-min_price
                    min_price = price
                    max_price = 0
                else:
                    max_price = price
        stonks += max(0, max_price-min_price)
        return stonks
```
<img width="1920" height="610" alt="image" src="https://github.com/user-attachments/assets/31bb36c5-2812-415c-a77e-ee7c21abbe0b" />

### Методология - Решение с помощью жадного алгоритма
В цикле для каждой текущей цены <kbd>price</kbd> происходят проверки:

- Если цена стала меньше текущего минимума и при этом не меньше максимума, обновляется минимум — начало новой "покупки".

- Иначе проверяется падение цены относительно максимума — значит, пора "продать" и зафиксировать прибыль: к <kbd>stonks</kbd> добавляется разница <kbd>max_price - min_price</kbd>, и лимиты (минимум и максимум) сбрасываются для следующей сделки.

- Если цена повышается, <kbd>max_price</kbd> обновляется — это потенциальный максимум для текущей сделки.

***

## Ответы на вопросы
1. Динамическое программирование - это метод решения сложных задач путем разбиения их на более простые подзадачи с последующим сохранением результатов этих подзадач, чтобы избежать повторных вычислений.

2. Big O() - это способ описания асимптотической сложности алгоритма, который показывает, как время выполнения или объем памяти растут в зависимости от размера входных данных.

3. Мемоизация в рекурсии - это техника оптимизации, при которой результаты вызова рекурсивных функций сохраняются, чтобы при повторных вызовах с теми же параметрами не выполнять вычисления заново, а использовать сохраненное значение.
