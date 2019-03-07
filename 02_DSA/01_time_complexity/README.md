# 시간복잡도



## 과제

아래 문제에 대한 답을 작성하기

#### 1. 다음 Big-O 표기법에 대하여 대소비교를 하시오. 

```
O(n), O(1), O(2^n), O(logn), O(n^2), O(10^n), O(n!), O(nlogn), O(n^10)
```



#### 2. 다음 함수들에 대하여 시간복잡도를 Big-O 표기법으로 표현하시오.

**2-1)**

```python
def func(n):
    n = 10
    return n
```

**2-2)**

```python
def func(n):
    ret = 0
    for i in range(n):
        ret += 1
    return retn
```

**2-3)**

```python
def func(n):
    ret = 0
    for i in range(n):
        for j in range(n):
            ret += 1
    return ret
```

**2-4)**

```python
def func(n):
    ret = 0
    for i in range(n):
        for j in range(i):
            ret += 1
    return ret
```

**2-5)**

```python
# data의 길이를 n이라고 가정
def func(data, x):
    lo = 0
    hi = len(data)
    while lo < hi:
        mid = (lo + hi) // 2
        if data[mid] == x:
            return mid
        elif data[mid] < x:
            lo = mid + 1
        else:
            hi = mid
    return None
```

**2-6)**

```python
def func(n):
    if n <= 0:
        return 1
    return func(n - 1) + func(n - 1)
```

**2-7)**

```python
def func(n, a=1, b=2):
    if n <= 1:
        print('{0}: {1} -> {2}'.format(n, a, b))
        return
    c = 6 - a - b
    func(n - 1, a, c)
    print('{0}: {1} -> {2}'.format(n, a, b))
    func(n - 1, c, b)
```



## 레퍼런스

[O(n), O(nlogn) 이런거 대체 무슨 뜻일까요?](https://www.youtube.com/watch?v=Y7KTRu6-XK0)

[빅오(Big-O)표기법 완전정복](https://www.youtube.com/watch?v=6Iq5iMCVsXA)

[시간복잡도와 공간복잡도(Time Complexity Space Complexity)](https://madplay.github.io/post/time-complexity-space-complexity)

[자료구조, 알고리즘 - 성능측정 (Big-O)](https://wayhome25.github.io/cs/2017/04/20/cs-26-bigO/)