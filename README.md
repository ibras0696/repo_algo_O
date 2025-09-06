Окей 👌 вот тебе компактная, но понятная **шпаргалка по Big-O**, с объяснением и кодом на Python.
Её можно держать под рукой при решении задач.

---

# 🔑 Шпаргалка по алгоритмическим сложностям

## O(1) — Константа

👉 Время не зависит от размера входа.
**Пример:** доступ к элементу списка по индексу.

```python
a = [1, 2, 3, 4, 5]
print(a[0])   # всегда 1 операция
```

---

## O(log n) — Логарифмическое

👉 Каждый шаг делим задачу пополам.
**Пример:** бинарный поиск.

```python
def binary_search(a, x):
    lo, hi = 0, len(a)-1
    while lo <= hi:
        mid = (lo+hi)//2
        if a[mid] == x:
            return mid
        if a[mid] < x:
            lo = mid+1
        else:
            hi = mid-1
    return -1
```

---

## O(n) — Линейное

👉 Один проход по всем данным.
**Пример:** сумма списка.

```python
def sum_list(a):
    total = 0
    for x in a:
        total += x
    return total
```

---

## O(n log n) — Линейно-логарифмическое

👉 Делим данные пополам (log n уровней) и на каждом уровне обрабатываем все n элементов.
**Пример:** быстрая/слияние сортировка.

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr)//2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)

def merge(l, r):
    result = []
    i = j = 0
    while i < len(l) and j < len(r):
        if l[i] < r[j]:
            result.append(l[i]); i += 1
        else:
            result.append(r[j]); j += 1
    result.extend(l[i:])
    result.extend(r[j:])
    return result
```

---

## O(n²) — Квадратичное

👉 Сравниваем каждый элемент с каждым.
**Пример:** поиск дубликатов «в лоб».

```python
def has_duplicates(a):
    for i in range(len(a)):
        for j in range(i+1, len(a)):
            if a[i] == a[j]:
                return True
    return False
```

---

## O(2ⁿ) — Экспоненциальное

👉 Количество вариантов удваивается при каждом шаге.
**Пример:** все подмножества.

```python
def subsets(nums):
    res = [[]]
    for x in nums:
        res += [s + [x] for s in res]
    return res
```

---

## O(n!) — Факториальное

👉 Все перестановки элементов.
**Пример:** все варианты порядка.

```python
import itertools
nums = [1, 2, 3]
perms = list(itertools.permutations(nums))
```

---

# 🚦 Как запоминать

* **O(1)** → мгновенно (хоть миллион данных).
* **O(log n)** → очень быстро, делим пополам.
* **O(n)** → нормально, линейно.
* **O(n log n)** → чаще всего сортировки.
* **O(n²)** → уже плохо, можно только для маленьких n.
* **O(2ⁿ), O(n!)** → переборы, почти всегда «невозможно» на больших входах.

---

Хочешь, я соберу для тебя ещё и **мини-таблицу «что использовать вместо чего»** (например, как заменить O(n²) на O(n) с помощью множества или хеша)?
