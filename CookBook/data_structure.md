
# 1.1 解压序列赋值给多个变量(作用可迭代对象)


```python
p = (4, 5)
x, y = p
```


```python
data = [ 'ACME', 50, 91.1, (2012, 12, 21) ]
name, shares, price, date = data
name, shares, price, (year, mon, day) = data
```


```python
s = 'Hello'
a, b, c, d, e = s
```


```python
# 变量个数和序列元素的个数不匹配，会产生一个异常
p = (4, 5)
x, y, z = p
```


```python
# 部分解压
data = [ 'ACME', 50, 91.1, (2012, 12, 21) ]
_, shares, price, _=data
```

# 1.2 解压可迭代对象赋值给多个变量


```python
record = ('Dave', 'dave@example.com', '773-555-1212', '847-555-1212')
record = ('Dave', 'dave@example.com')
record = ('Dave', 'dave@example.com','773-555-1212', '847-555-1212','773-555-1213', '847-555-1213')
name, email, *phone_numbers = record
phone_numbers
```


```python
#星号表达式也能用在列表的开始部分
*trailing, current = [10, 8, 7, 1, 9, 5, 10, 3]
trailing
current

trailing, *current = [10, 8, 7, 1, 9, 5, 10, 3]
trailing
current
```


```python
line = 'nobody:*:-2:-2:Unprivileged User:/var/empty:/usr/bin/false'
uname, *fields, homedir, sh = line.split(':')
```

# 1.3 双向队列


```python
from collections import deque


q = deque(maxlen=3)
q.append(1)
q.append(2)
q.append(3)
q.append(4)
q.append(5)
#q.appendleft(6)  ###默认从右边
```


```python
q.pop() #队尾元素删去
q.popleft() #队头元素删去
```


```python
#在队列两端插入或删除元素时间复杂度都是 O(1) ，
#而在列表的开头插入或删除元素的时间复杂度为 O(N) 。
```

 # 1.4 查找最大或最小的 N 个元素(heapq)


```python
#该模块提供了堆排序算法的实现,heapq有两种方式创建堆， 一种是使用一个空列表，
#然后使用heapq.heappush()函数把值加入堆中，另外一种就是使用heap.heapify(list)转换列表成为堆结构
```


```python
import heapq


nums = [2, 3, 5, 1, 54, 23, 132]
heap = []
for num in nums:
    heapq.heappush(heap, num)  # 加入堆

print(heap[0])  # 如果只是想获取最小值而不是弹出，使用heap[0]
print([heapq.heappop(heap) for _ in range(len(nums))])  # 堆排序结果
```


```python
heap= []
nums = [2, 3, 5, 1, 54, 23, 132]
heapq.heapify(nums)
print([heapq.heappop(heap) for _ in range(len(nums))])
```


```python
import math
from io import StringIO


def show_tree(tree, total_width=36, fill=' '):
    """Pretty-print a tree."""
    output = StringIO()
    last_row = -1
    for i, n in enumerate(tree):
        if i:
            row = int(math.floor(math.log(i + 1, 2)))
        else:
            row = 0
        if row != last_row:
            output.write('\n')
        columns = 2 ** row
        col_width = int(math.floor(total_width / columns))
        output.write(str(n).center(col_width, fill))
        last_row = row
    print(output.getvalue())
    print('-' * total_width)
    print()
```


```python
data = [19, 9, 4, 10, 11]
heap = []
print('random :', data)
print()

for n in data:
    print('add {:>3}:'.format(n))
    heapq.heappush(heap, n)
    show_tree(heap)
```
  
